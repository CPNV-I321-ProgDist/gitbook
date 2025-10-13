# Couche de présentation

## Intention

Démontrer à l'aide d'un code, un exemple d'implémentation de la couche de présentation.

En complément à la théorie dédiée aux [différentes couches d'une API](../).

On y aperçoit :

* le routage de base réalisé par "router.js"
* le routage spécifique à une ressource réalisé par "produc.js"
  * la documentation d'open API pour générer le SWAGGER tout comme,
  * le travail de redirection qui est opérée après une validation de la présence des paramètres ainsi que leur format.

## Exemple

```javascript
// routes/router.js
const express = require('express');
const productsRouter = require('./products');

const router = express.Router();

router.use('/products', productsRouter);

module.exports = router;
```

```javascript
// routes/products.js
const express = require('express');
const { body, param } = require('express-validator');
const productController = require('../controllers/productController');

const router = express.Router();

//Documentation pour le SWAGGER

/**
 * @openapi
 * /api/products:
 *   get:
 *     summary: Retrieve a list of products
 *     responses:
 *       200:
 *         description: A list of products
 *   post:
 *     summary: Create a new product
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             type: object
 *             required:
 *               - name
 *               - price
 *             properties:
 *               name:
 *                 type: string
 *               description:
 *                 type: string
 *               imageUrl:
 *                 type: string
 *               price:
 *                 type: number
 *     responses:
 *       201:
 *         description: Product created
 *       400:
 *         description: Invalid input
 */

/**
 * @openapi
 * /api/products/{id}:
 *   get:
 *     summary: Get a product by ID
 *     parameters:
 *       - in: path
 *         name: id
 *         required: true
 *         schema:
 *           type: integer
 *     responses:
 *       200:
 *         description: A single product
 *       404:
 *         description: Product not found
 *   put:
 *     summary: Update a product by ID
 *     parameters:
 *       - in: path
 *         name: id
 *         required: true
 *         schema:
 *           type: integer
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             type: object
 *             properties:
 *               name:
 *                 type: string
 *               description:
 *                 type: string
 *               imageUrl:
 *                 type: string
 *               price:
 *                 type: number
 *     responses:
 *       200:
 *         description: Product updated
 *       400:
 *         description: Invalid input
 *       404:
 *         description: Product not found
 *   delete:
 *     summary: Delete a product by ID
 *     parameters:
 *       - in: path
 *         name: id
 *         required: true
 *         schema:
 *           type: integer
 *     responses:
 *       204:
 *         description: Product deleted
 *       404:
 *         description: Product not found
 */

/**
 * Validation rules
 */
const createAndUpdateValidations = [
    body('name').isString().notEmpty().withMessage('name is required'),
    body('description').optional().isString(),
    body('imageUrl').optional().isString().isURL().withMessage('imageUrl must be a valid URL'),
    body('price').isFloat({ gt: 0 }).withMessage('price must be a positive number'),
];


//Après la validation, la redirection vers le contrôleur dédiée
router.get('/', productController.findAll);
router.post('/', createAndUpdateValidations, productController.create);
router.get('/:id', [param('id').isInt().withMessage('id must be an integer')], productController.findOne);
router.put('/:id', [param('id').isInt().withMessage('id must be an integer'), ...createAndUpdateValidations], productController.update);
router.delete('/:id', [param('id').isInt().withMessage('id must be an integer')], productController.delete);

module.exports = router;

```
