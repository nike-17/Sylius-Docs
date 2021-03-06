VariantGenerator
================

This is used to create all possible combinations of an object's options and to create ``Variant`` models from them.

**Example:**

If an object such as a t-shirt has 2 options - *Color* and *Size* - with 3 possible values per option,
then the generator will create 9 variants and assign them to the object.

The generator will ignore invalid variants or variants that already exist.

**T-Shirt Options**

+------------+----------+
| **Colors** | **Size** |
+------------+----------+
| Black      | Small    |
+------------+----------+
| White      | Medium   |
+------------+----------+
| Red        | Large    |
+------------+----------+

**Possible T-Shirt Variants**

These variants should be generated by the ``VariantGenerator`` from the options above.

1. Black, Small
2. Black, Medium
3. Black, Large
4. White, Small
5. White, Medium
6. White, Large
7. Red, Small
8. Red, Medium
9. Red, Large


**The Code**

.. code-block:: php

    use Sylius\Component\Resource\Repository\RepositoryInterface;
    use Sylius\Component\Variation\Generator\VariantGenerator;
    use Sylius\Component\Variation\Model\VariableInterface;
 
    /** @var RepositoryInterface $variantRepository */
    $variantRepository = /*...*/
    
    /**
     * From the example above, this would be the T-Shirt product.
     *
     * @var VariableInterface $variable
     */
    $variable = /*...*/

    $generator = new VariantGenerator($variantRepository);

    // Generate all possible variants if they don't exist currently.
    $generator->generate($variable)

.. note::

    The variant generator implements ``Sylius\Component\Variation\Generator\VariantGeneratorInterface``.
