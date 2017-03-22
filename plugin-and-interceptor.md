# Plugin and Interceptor

## Description

The Plugin-Interceptor solution provides a secure and clean way to extend the core features of Magento avoid Observers and Overwritten classes.

Interceptor is a general object oriented software design pattern to provide secure access to another classes and manipulate their public methods. The Interceptor pattern is implemented in Magento as a core feature.

Plugin is a Magento 2 feature, it is a single class configured from di.xml. Plugins automatically generate Interceptors.

## Overview

* Namespace of Vendor's Plugin class MUST has to follow the subject class namespace.
* Plugin class name and the subject class name MUST be identical.
* Plugin class MUST be in the Plugin namespace.
* The plugin tag's name parameter in the Configuration di.xml SHOULD contains the vendor's module PSR 2 name as the first part. The second part SHOULD be from the subject class name and its namespace in lowercase separated by underscores. The two parts SHOULD be connected by the PHP Scope Resolution Operator.

## Example

**Plugin class:**

```php
<?php

namespace Vendor\Module\Plugin\Magento\Sales\Model;
 
class Order
{
    
}
```

**di.xml:**

```xml
<?xml version="1.0"?>

<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
        
    <type name="Magento\Sales\Model\Order">
        <plugin name="Vendor_Module::magento_sales_model_order"
                type="Vendor\Module\Plugin\Magento\Sales\Model\Order" />
    </type>
        
</config>
```