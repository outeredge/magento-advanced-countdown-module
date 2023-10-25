# outer/edge Advanced Countdown Module for Magento 2

**[View on Magento Marketplace](https://commercemarketplace.adobe.com/outeredge-magento-advanced-countdown-module.html)**

Improve your site and generate more sales. Create urgency by showing a countdown timer on the product page to let customers know how long they have to order the product before the shipping deadline.

In addition to the countdown timer, this extension can give the customer full transparency of a product's stock status. Based on the product's parameters, you can show different stock statuses such as "Available Soon" or "Special Order", instead of just "In Stock" and "Out of Stock".

The stock messages and countdown timer messages can be customised to show your own wording. Following best practices, this extension can be installed and used out of the box or customised to work with your own custom theme.

### Features

* Display shipping countdown timer.
* Show details stock status, for example, available to order, backoder, expected restock date.
* Add custom countdown timer messages in Magento configuration
* Add restricted shipping dates for public holidays
* Works for simple, configurable and bundle products
* Works with third-party shipping modules such as **Amasty Shipping Table Rates**

| **Countdown timer on product page:**  | **Countdowm timer for preorder product:** |
| ------ | ------ |
| ![Product Page Countdown Timer](/assets/screenshot-product-zoom.png) | ![Product Page Countdown Timer](/assets/screenshot-product-preorder.png) |

**[Buy outer/edge Magento 2 Countdown Timer on Magento Marketplace](https://commercemarketplace.adobe.com/outeredge-magento-advanced-countdown-module.html)**

# Installation

## Install via Composer

```
composer require outeredge/magento-advanced-countdown-module
```

# Configuration

Configuration is available in `Stores > Configuration > outer/edge > Delivery Countdown`. The following options are available:

### Countdown Timer Settings

* **Enable:** Enable or disable the module functionality
* **Timer cutoff hour (24hr):** The cutoff hour time for shipping in 24 hour format, for example for 2PM, use "14"
* **Timer cutoff minute:** The cutoff minute for shipping. Value can be a number from 0-59, for example for 2:30 PM, set value to "30"
* **Show seconds:** If set to "Yes", the countdown timer will include seconds on the frontend, otherwise will just show hours and minutes.
* **Hide timer after cutoff time:** If set to `Yes`, the countdown timer block will be hidden after the cuttoff time is reached. Otherwise it will stay and countdown to the next cutoff time (ie the following day).
* **Enabled Availability Types:** Select which delivery types are enabled. This will adjust the stock status. See the "Delivery Types" table below for more details.
* **Restricted Dispatch Days:** Select which days orders are not dispatched, for example if you do not dispatch on weekends select 'Saturday' and 'Sunday'.
* **Restricted Delivery Days:** Select the days when delivery is not available, for example if you do not deliver on Sunday. If the delivery time for the shipping rate is non-numeric (ie "sat" or "sun") this will be ignored.
* **Special Order Calculation Method:** `Automatic` will assume that products with a "Dispatch Time" and a positive stock level are special order items. If set to `Special Order Attribute` only manually specified products have a "Special Order" stock status.

#### Availability Types

The table below describes the Availability Types and how the combination of a product's stock status and attribute values affects the message which is displayed to the customer. The Availability Types can be enabled or disabled via the `Enabled Availability Types` configuration option, and the corresponding messages customised via the `Countdown Messages` configuration.

| Availability Type | Product Stock | Backorders enabled | Estimated dispatch Date * | Estimated dispatch Days * | Special Order * |
| ------ | ------ | ------ | ------ | ------ | ------ |
| In stock | >=1 | Y/N | N | N | N |
| Spcial Order  | 1+ | N | N | Y | N |
| Preorder | <=0 | Y | Y/N | (ignored) | N |
| Coming soon (no preorder) | 0 or Out of Stock | N | Y/N | -1 | N |
| Out of stock | 0 or Out of Stock | N | N | N | N |

> Headings marked with an asterisk (*) refer to product attributes created when installing the module.

### Countdown Messages

Customise the frontend title and message for the enabled stock statuses.

* **Title:** This will be displayed where the "In Stock"/"Out Of Stock" message is usually shown.
* **Message:** This message will be shown on the countdown timer itself. Placeholders are available to allow you to fully customise your countdown messages.

#### Stock Message Placeholders

* **{date}** Delivery date based on fastest shipping method
* **{timer}** The countdown timer
* **{method}** The fastest delivery method

#### Defaults

| Availability Type | Title | Message |
| ------ | ------ | ------ |
| In Stock | In Stock  | Want it {date}? Order it within {timer} and choose {method} at checkout |
| Preorder | Available to Preorder | Expected available date: {date} |
| Special Order | Special Order | Special order item, order now to get it {date} |
| Coming Soon | Coming Soon | Coming soon, expected {date} |
| Out Of Stock | Out Of Stock | *empty* |

![Configuration](/assets/screenshot-config.png)

# Product Attributes

When the module is installed, some new product attributes are created. Refer to the table above the see how the values of these attributes affect the stock and countdown messages:

* **Estimated Dispatch Date** - The date which you expect the product to be avaiable again.
* **Estimated Dispatch Days** - The number of days that you expect the pass before the product is available. For example if the product is a special order item.
* **Special Order** - If the item is a special order item, for example if it is not kept in stock and ordered on request.

# Restricted Dates

`Sales > Restricted Dates`

You can add dates that you would like to be ingnored such as public holidays or any other date to the `Restricted Dates` grid. These will be taken into account when calculating the estimated delivery date:

![Restricted Dates](/assets/screenshot-restricted-dates.png)

# Shipping Method Delivery Times

`Sales > Shipping Method Delivery Times`

For each of your shipping methods you can optionally add a delivery time. Adding a delivery time to the method will allow an estimated delivery date to be shown to the customer for each method in the checkout. It will also be used to calculate the fastest delivery method for the countdown timer.

![Shipping Method Delivery Times](/assets/screenshot-shipping-method-delivery-times.png)


**[Buy outer/edge Magento 2 Countdown Timer on Magento Marketplace](https://commercemarketplace.adobe.com/outeredge-magento-advanced-countdown-module.html)**
