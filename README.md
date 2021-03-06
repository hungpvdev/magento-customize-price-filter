# Magento - Customize Price Filter extension

## Overview

Magento is able to display price ranges in the layered navigation. It offers 3 ways to calculate price step. But none of them allows to specify exactly the price ranges you want to see.

Another point is that Magento subtracts 0.01 to the highest value of each price range when displaying them. I.e. if range is "100-200", Magento will display "100.00 - 199.99".

This extension allows you to set the exact price ranges you need and to disable subtraction of 0.01.

## Compatibility

Tested on Magento CE 1.6 - 1.9

Michele Marcucci forked v1.0 of this module to make a [compatibility fix for Magento CE 1.5](https://github.com/michelem09/MagentoCustomizePriceFilter). Current version of this module should be already compatible (not tested).

## Notes

* Free and open source
* Fully configurable
* Bundled with English and French translations

## Installation

No Magento files will be modified but following classes will be extended and some of their methods overridden:

* Mage\_Catalog\_Model\_Layer\_Filter\_Price
* Mage\_Catalog\_Model\_Resource\_Layer\_Filter\_Price

### Manually

* Download the latest version of this module [here](https://github.com/aurmil/magento-customize-price-filter/archive/master.zip)
* Unzip it
* Move the "app" folder into the root directory of your Magento application, it will be merged with the existing "app" folder

### With modman

* ```$ modman clone git@github.com:aurmil/magento-customize-price-filter.git```

### With composer

* Adapt the following "composer.json" file into yours:

```
{
	"require": {
		"aurmil/magento-customize-price-filter": "dev-master"
	},
    "repositories": [
        {
            "type": "composer",
            "url": "http://packages.firegento.com"
        },
        {
            "type": "vcs",
            "url": "git://github.com/aurmil/magento-customize-price-filter"
        }
    ],
	"extra": {
		"magento-root-dir": "./"
	}
}
```

* Install or update your composer project dependencies

## Usage

In __System > Configuration > Catalog > Catalog > Layered Navigation__, this extension adds two new options: __Price Ranges__ and __Subtract 0.01 from the highest value of each price range__

![](http://4.bp.blogspot.com/-ubCE1QQ-XSs/UHkh7AbIvBI/AAAAAAAALMg/dACSlC0T6Xw/s1600/price-ranges.png)

This option is only available if you choose __Manual__ for __Price Navigation Step Calculation__.

__Note about the screenshot:__ you can see a semicolon at the end of the field. This is just because the value continues on the right, this is not the last character.

You have to stick to this format:

* ; separates prices ranges
* - separates min and max values of a given range
* min value of the first range and max value of the last range are optional. Magento will respectively display "Under [max1]" and "[minN] and above".

Leaving this field empty means stay with the Magento basic behavior for manual calculation.

![](http://1.bp.blogspot.com/-IySUPzoaAls/UHkijgjwwPI/AAAAAAAALMo/f0oaG3zQzKo/s1600/substract-001.png)

This option is available regardless of the value set for __Price Navigation Step Calculation__.

* Select "Yes" (default value) to stay with the Magento basic behavior
* Select "No" to disable subtraction of 0.01

In __Catalog > Manage Categories__, this extension adds a new category attribute: __Price Ranges__ in the __Display Settings__ tab panel.

![](http://1.bp.blogspot.com/-tpY23PoFlSs/VEe393Ml79I/AAAAAAAARyo/mWC7SL9yc6o/s1600/display-settings.png)

This attribute allows you to override the price ranges configuration option for each catalog category. It will be considered when browsing the corresponding category frontend page.

Leaving this field empty means using the price ranges configuration option.

## Changelog

### 2.0

* Add possibility to set price ranges per catalog category

### 1.4

* Fix for product count, with "Maximum Number of Price Intervals"

### 1.3

* Magento CE 1.8 and 1.9 compatibility checked
* Various minor changes and fixes

### 1.2

* Magento CE 1.6 compatibility

### 1.1

* some minor corrections

### 1.0

* initial release
