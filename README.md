# Installing magerun
`curl -O https://files.magerun.net/n98-magerun2.phar && chmod +x ./n98-magerun2.phar`

Paste `local.xml` in app/etc/ for **n98 mage run**
then enter your credentials of `env.php` into `local.xml` fields.

## Remove only products.
`./n98-magerun2.phar db:dump --strip="catalog_product*"`

## Remove categories
Run n98 dev console.

> NOTE: This removes the categories present in current database. This DOESN'T create a dump file.

`./n98-magerun dev:console`

```
$di->get(\Magento\Framework\App\State::class)->setAreaCode('adminhtml');
$di->get(\Magento\Framework\Registry::class)->register('isSecureArea', true);
$di->get(\Magento\Catalog\Model\Category::class)->getCollection()->addAttributeToFilter('entity_id', ['gt' => 2])->delete();
```

## Get Category ID and Category name
Below code snippets fetches and deletes all the categories except root and master catalog category.
NOTE: master catalog category can have different categoryId than the one specified here, comment out the delete function and get the appropriate id for master catalog.
```
$objectManager =  \Magento\Framework\App\ObjectManager::getInstance();
$categoryCollection = $objectManager->get('\Magento\Catalog\Model\ResourceModel\Category\CollectionFactory'); $categories = $categoryCollection->create(); $categories->addAttributeToSelect('*');


foreach($categories as $category){
$catName = $category->getName();
$catId = $category->getId();
echo "$catId ---> $catName \n";
if($catId <= 2 || $cat == 9079) continue;
// Skip the root category and master catalog category(Generated from akeneo)

$category->delete();
}

```
