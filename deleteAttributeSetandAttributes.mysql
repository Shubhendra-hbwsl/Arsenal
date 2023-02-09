INSERT INTO `catalog_product_link_type` (`link_type_id`, `code`) VALUES (1, 'relation'), (3, 'super'), (4, 'up_sell'), (5, 'cross_sell');

INSERT INTO `catalog_product_link_attribute` (`product_link_attribute_id`, `link_type_id`, `product_link_attribute_code`, `data_type`) VALUES (1, 1, 'position', 'int'), (2, 4, 'position', 'int'), (3, 5, 'position', 'int'), (4, 3, 'position', 'int'), (5, 3, 'qty', 'decimal');



SET FOREIGN_KEY_CHECKS = 1;
delete from eav_attribute_set where attribute_set_id != 2;
DELETE options FROM eav_attribute AS attribute INNER JOIN eav_attribute_option AS options ON attribute.attribute_id = options.attribute_id WHERE attribute.entity_type_id = 4;

delete from eav_attribute where is_user_defined = 1;
