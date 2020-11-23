# Integrate Midtrans Snap to E-Commerce Content Management System
<hr>

Content Management System (CMS) allows you to easily have a website/web store without building from scratch. CMS does not require programming knowledge. You just need to install the CMS and customize according your requirement. You only require to manage the content (Content Management). Some of the examples of CMS are WordPress, Magento 2, PrestaShop, WHMCS, and so on.

## Preparation
<br>

<div class="my-card">

#### [Sign Up for Midtrans Account](/en/midtrans-account/overview.md)
Sign up for a Midtrans Merchant Administration Portal (MAP) account, to get your API Keys for *Sandbox* environment and to test integration.
</div>

<div class="my-card">

#### [Retrieve API Keys](/en/midtrans-account/overview.md#retrieving-api-access-keys)
Retrieve API Keys for *Sandbox* environment that will be used for this guide.
</div>

?>***Note***: Follow the [preparation section](#preparation) to retrieve *Client Key* and *Server Key*, before proceeding to the section given below.

## CMS Plugins and Extensions Supported by Midtrans
A list of Content Management System (CMS) plugins and extensions, supported by Midtrans, is given below.

<br>
<div class="my-card">
<!-- NOTE: "Space" is intentionally added as prefix, to avoid header ID conflict-->

#### [ WordPress - WooCommerce](#wordpress-woocommerce)
</div>

<div class="my-card">

#### [ Magento](#magento)
</div>

<div class="my-card">

#### [ PrestaShop](#prestashop)
</div>

<div class="my-card">

#### [ OpenCart](#opencart)
</div>

<div class="my-card">

#### [ WHMCS](#whmcs)
</div>

<div class="my-card">

#### [ Drupal](#drupal-8)
</div>

<div class="my-card">

#### [ WordPress - Easy Digital Download](#wordpress-easy-digital-download)
</div>
<!-- TODO: explain what is notification URL for non dev user. Why it is important, and what's the benefit of using notification url -->

<hr><br><br>

## Steps for Integration
Step-by-step guide to install Snap integration plugins to your CMS of choice, is given below.

## WordPress - WooCommerce

<hr>

Midtrans ❤️ WooCommerce! The plugin allows secure online payment on your WooCommerce store, without ever needing your customer to leave your WooCommerce store! It has a beautiful built-in responsive payment interface. Midtrans strives to make payments simple for you and your customers. It supports various online payment channels. Midtrans supports WooCommerce v2 and v3.

Midtrans WooCommerce plugin is also available on [WordPress plugins store](https://wordpress.org/plugins/midtrans-woocommerce/). If you cannot find it listed there, you can always download and install it manually. For more details, refer to [Manual Installation](#manual-installation).

### Requirements
Some of the requirements to continue with the integration process, are listed below.
* WordPress v3.9 or later **|** Tested up to v5.x
* WooCommerce v2 or later **|** Tested up to v3.5.2
* PHP version v5.4 or later
* MySQL version v5.0 or later
* PHP CURL enabled server/host
* Midtrans plugin for WooCommerce [ [GitHub](https://github.com/veritrans/SNAP-Woocommerce) | [Zip](https://github.com/veritrans/SNAP-Woocommerce/archive/master.zip) ]

### Installing WooCommerce Plugin
Select **any one** of the installation options given below.

#### **Simple Installation**

To install Midtrans WooCommerce plugin, follow the steps given below.
  1. Login to your WordPress administration panel.
  2. Go to **Plugins** menu.
  3. Click **add new**.
  4. Search for **Midtrans-WooCommerce plugin**.
  5. Click **Install Now** and follow on-screen instructions.
  6. Proceed to [Configuring Midtrans WooCommerce Plugin](#configuring-midtrans-woocommerce-plugin).

If you are unable to install, proceed to [Manual Installation](#manual-installation).

#### **Manual Installation**

To install Midtrans-WooCommerce plugin manually, follow the steps given below.
   1. Download the Midtrans plugin for WooCommerce.
   2. Extract the plugin, then rename the modules folder as **midtrans-woocommerce**.
   3. Upload the unzipped plugin folder to your WordPress installation's `./wp-content/plugins/` directory.
   4. **Install and activate** the plugin from plugins menu within the WordPress administration panel.
   5. Proceed to [Configuring Midtrans WooCommerce Plugin](#configuring-midtrans-woocommerce-plugin).

### Configuring WooCommerce Plugin
To configure WooCommerce plugin, follow the steps given below.
1. Go to **WooCommerce > Settings > Payments > Midtrans** menu.
2. Enter **Title**. This text appears on the button displayed to the customer.
3. Select **Environment** from dropdown. `Sandbox` for testing transaction and `Production` for real transaction.
4. Enter **Merchant ID**.
5. Enter **Client Key**.
6. Enter **Server key**.
   For more details, refer to [Preparation](/en/snap/preparation.md).

?>***Note***: Other fields are optional.

![WooCommerce Install](./../../asset/image/WooCommerce-install.gif)


### Configuring WooCommerce Plugin Notification
To configure the WooCommerce plugin notification URL, follow the steps given below.
1. Login to your MAP account.
2. Select the **Environment** from drop-down list.
3. On the Home page, go to **SETTINGS > CONFIGURATION**.
   *Configuration* page is displayed.
4. Enter **Payment Notification URL**.
5. Enter **Finish Redirect URL**.
6. Enter **Error Redirect URL**.
7. Enter **Unfinish Redirect URL**.
8. Click **Update**.
   A confirmation message is displayed.

WooCommerce plugin notification is configured.

Table given below describes the fields and the URL.

| Label | URL Role | Redirect URL|
|----------|-------------|-------------|
| 1 | Payment Notification URL | [your-site-url]/?wc-api=WC_Gateway_Midtrans |
| 2 | Finish Redirect URL | [your-site-url]/?wc-api=WC_Gateway_Midtrans |
| 3 | Unfinish Redirect URL | [your-site-url]/?wc-api=WC_Gateway_Midtrans |
| 4 | Error Redirect URL | [your-site-url]/?wc-api=WC_Gateway_Midtrans |

?>***Note***: WordPress is installed in `your-site-url`. It can be the domain root directory such as `https://myshop.com` or `https://shop.myshop.com`or within a sub directory such as `https://myshop.com/wordpress/`.<br>Please make sure to input **http://** or **https://** in *Notification URL* and *Redirect URL*, based on your web-server configuration.<br>If you are not sure, open your web URL in a browser, and check the URL is **http** or **https** on the address bar.

<details>
<summary>

### Transaction Test
</summary>

<article>
1. Perform successful transaction on your online store by entering the card details given below.


| Name        | Value               |
| :---------- | :------------------ |
| Card Number | 4811 1111 1111 1114 |
| CVV         | 123                 |
| Exp Month   | 01                  |
| Exp Year    | 2025                |
| OTP/3DS     | 112233              |

For more details, refer to [Testing Payments on Sandbox](/en/technical-reference/sandbox-test).

2. Examine a few points below to ensure plugin is installed and performs properly.

Check Point| Error |Troubleshooting
--- | --- | ---
Order status in CMS backend| Order status not recorded in the backend. | Check endpoint/Payment Notification URL setting on MAP.<br> Check if your CMS/Notification URL is publicly accessible.
Merchant email notification| Notification not received. | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications).
Customer email notification| Notification not received. | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications).

### Payment Example
![WooCommerce Payment Test](./../../asset/image/woo-pay-show.gif)

</article>
</details>

For more details and configurations, refer to [Midtrans WooCommerce wiki documentation](https://github.com/veritrans/SNAP-Woocommerce/wiki).
<hr><br><br>

## Magento
<hr>

Midtrans ❤️ Magento! Midtrans takes customer experience (UX) seriously and tries to make payments simple for you and the customers. With this plugin you can make your Magento store using Midtrans payment. This extension also available on [Magento Marketplace](https://marketplace.magento.com/midtrans-snap.html).

?>***Note***: This section explains the installation and the configuration for Magento 2. For Magento 1, please refer to [Snap Plugin for E-commerce CMS](/en/technical-reference/library-plugin.md#snap-plugin-for-e-commerce-cms)

### Requirements
Some of the requirements to continue with the integration process, are listed below.
* An online store with Magento infrastructure
*  Magento2 version 2.1.0, 2.2.0, 2.3.4 and later | Tested up to v2.3.4
* PHP v5.6 or later
* MySQL v5.7 or later
* Midtrans plugin for Magento; For Magento v2.x [ [GitHub](https://github.com/Midtrans/Midtrans-Magento2) | [Zip](https://github.com/Midtrans/Midtrans-Magento2/archive/master.zip) ], For Magento v1.9 [ [GitHub](https://github.com/veritrans/SNAP-Magento) | [Zip](https://github.com/veritrans/SNAP-Magento/archive/master.zip) ]

### Installing Magento Plugins

To install Magento plugin, select **any one** of the installation options given below.

#### Installing plugin through Magento Marketplace
You can install Midtrans Snap plugin through Magento Marketplace. Please visit Midtrans on [Magento Marketplace](https://marketplace.magento.com/midtrans-snap.html) and follow step-by-step installation instructions from the [Official Magento extension docs](https://docs.magento.com/user-guide/system/web-setup-extension-manager.html).

#### Installing plugins through Composer
Install Composer and create Magento Marketplace account before installing Midtrans Snap plugin through Composer.


On your terminal, go to the Magento folder and run the commands given below.
1. Install the plugins: `composer require midtrans/snap`.
2. Enable the plugin: `bin/magento module:enable Midtrans_Snap`.
3. Execute upgrade script : `bin/magento setup:upgrade`.
4. Flush cache storage : `bin/magento cache:flush`.
5. Login to your Magento administration Panel.
6. Proceed to [Configuring Magento 2 Plugin](#configuring-magento-2-plugin) section.

#### Installing plugins from GitHub project
To customize Midtrans Magento plugin to handle your business model, follow the steps given below.
1. Download and extract the plugin you have previously downloaded from GitHub and rename the folder as Snap.
2. Make a directory structure as shown below.

![Magento folder structure](./../../asset/image/magento-folder-structure.png)

3. Locate the root Magento directory of your shop via FTP connection.
4. Copy the app folders into the Magento root folder.
5. Run the following commands on terminal.
    * `bin/magento module:enable Midtrans_Snap`
    * `bin/magento setup:upgrade`
    * `bin/magento cache:flush`
6. Login to your Magento administration panel.
7. Proceed to [Configuring Magento 2 Plugin](#configuring-magento-2-plugin) section.

### Configuring Magento 2 Plugin
Before you begin, install and enable Midtrans Snap plugin.

To configure the Midtrans plugin in your Magento administration panel, follow the steps given below.
1. Login to your Magento administration panel.
2. Go to **Stores(1)** > **Configuration(2)**.
3. Go to **Sales(3)** > **Payment Methods(4)**.
![Magento 2 step config 1](./../../asset/image/Magento2-7.png)

4. In the **Midtrans - Accept Online Payment** section, click **Basic Settings** and fill out the fields given below.

| Field                   | Description                                                  |
| :---------------------- | :----------------------------------------------------------- |
| Is Production           | Select whether you want to use a *Sandbox* or *Production* environment. |
| Merchant ID             | Unique id of your Midtrans account for which the payments will be processed. |
| Sandbox \- ClientKey    | Used as an API key to be used for authorization *Sandbox* environment on frontend API request/configuration\. So, it is safe to put in your HTML / client code publicly. |
| Sandbox \- ServerKey    | Used as an API key to be used for authorization *Sandbox* environment while calling Midtrans API from the backend. So, keep it stored confidentially. |
| Production \- ClientKey | Used as an API key to be used for authorization *Production* environment on frontend API request/configuration. So, it is safe to put in your HTML / client code publicly. |
| Production \- ServerKey | Used as an API key to be used for authorization *Production* environments while calling Midtrans API from the backend. So, keep it stored confidentially |
| Enable Snap redirect    | Change to Snap redirect mode, the default value is **No**.   |

?>***Note***: *Access Key* and *Server Key* are unique for every merchant. Always keep *Server Key* confidential.

### Storing Log Files
The plugin will store log files in directory `/var/log/midtrans`. By default, the log files are enabled for request, notification and error log. Throw Exception log is disabled by default.
![magento_log_options](./../../asset/image/magento-log-options.png)


### Configuring Payment Integration
To use Snap payment method, select any one of the options given below.

#### **Snap payment integration**

This is the default payment for Midtrans Magento plugin. Snap payment is enabled automatically when Midtrans plugin is installed. Midtrans shows the available payment method on the Snap payment screen.

#### **Specific payment integration | Optional**

Enabling this feature will display additional payment options to the customer. For specific payment that is specified in the **Allowed Payment Method** field, Midtrans Snap will show only the listed payment method on the Snap screen.

#### **Online Installment payment integration | Optional**

Enabling this feature will display additional payment options to the customer, for *Online Installment* payment where the *Card Issuer* and *Acquiring Bank* is the same entity. For example, if a customer makes an installment payment using BNI Card and the *Acquiring Bank* is also BNI.

#### **Offline Installment payment integration | Optional**

Enabling this feature will display additional payment options to customer, for *Offline Installment* where the *Card Issuer* and *Acquiring Bank* don't have to be same entity. For example, if a customer makes an installment payment using BNI Card and the *Acquiring Bank* is Mandiri.

?>***Note***: You can use different Midtrans Account for every Snap model payment method. To do so, configure the *Access Key* in Optional section `“Use different Midtrans account”`. If the optional *Access Key* is empty, the plugin will automatically use *Access Key* on Basic Settings.<br>Currently, the built-in BCA KlikPay landing page only use *Server Key* from basic settings of Snap payment integration.

<details>
<summary>

### Customizing Configuration
</summary>
The table given below describes the fields to customize configurations.

<article>

| Field                  | Description  |
|-----------------------|--------------------------------------------------------------------------|
| Enable                 | Payment snap section enable.  |
| Title                  | The title for the payment method in the checkout page. |
| Custom Expiry          | This field will allow you to set a custom duration on how long the transaction is available to be paid\. |
| Allowed Payment Method | Customize allowed payment method, separate payment method code with a comma\. For example, bank\_transfer, credit\_card\. Leave it as default if you are not sure\.  |
| Acquiring Bank         | You can specify which Acquiring Bank they prefer to use for a specific transaction\. The transaction fund will be routed to that specific acquiring bank\. Leave it blank if you are not sure.     |
| BIN Number             | It is a feature that allows the merchant to accept only Credit Cards within a specific set of BIN numbers\. Separate BIN number with comma. For example, `4,5,4811,bni,mandiri`\. Leave it blank if you are not sure. |
| Installment Terms      | An arrangement for payment by installments\.     |
| 3D Secure              | You must enable 3D Secure for secure card transactions\. Please contact us if you wish to disable this feature in the *Production* environment\.   |
| Save Card              | This will allow your customer to save their card on the payment popup, for faster payment flow on future transactions. |

</article>
</details>

### Configuring Magento 2 Plugin Notification
To configure the Magento 2 plugin notification URL, follow the steps given below.
1. Login to your MAP account.

2. Select the **Environment** from drop-down list.

3. On the Home page, go to **SETTINGS > CONFIGURATION**.
   *Configuration* page is displayed.
   
   ​	* Enter **Payment Notification URL**.
   
   ​	* Enter **Finish Redirect URL**.
   
   ​	* Enter **Error Redirect URL**.
   
   	*  Enter **Unfinish Redirect URL**
   	*  Click **Update**.
   
4. On the Home page, go to **SETTINGS > SNAP PREFERENCES > System settings**.

   ​	* Enter **Finish Redirect URL**.

   ​	* Enter **Error Redirect URL**.

    * Enter **Unfinish Redirect URL**.
   
    * Click **Save**.
   
      A confirmation message is displayed.
      Magento 2 plugin notification is configured.

The table given below shows the fields and the redirect URL.

| Field                    | Redirect URL                              |
| ------------------------ | ----------------------------------------- |
| Payment Notification URL | [your-site-url]/snap/payment/notification |
| Finish Redirect URL      | [your-site-url]/snap/index/finish         |
| Error Redirect URL       | [your-site-url]/snap/index/finish         |
| Unfinish Redirect URL    | [your-site-url]/snap/index/finish         |



?> ***Note***: Please make sure to enter **http://** or **https://** in Notification URL and Redirect URL, according to your web-server configuration.<br>If you are not sure, open your web URL in a browser, and check the URL is **http** or **https** on the address bar.

<details>
<summary>

### Refunding Transactions Online
</summary>
You can request refunds either from the Midtrans Dashboard or from the Magento administration. After a refund is issued, it cannot be cancelled or undone. So, before you trigger a refund request, make sure to check the refund amount and any other details. The online refund feature is available for GoPay and credit card payment methods.

If you make refund from the Midtrans *Dashboard*, Refund notification is sent to Magento, transaction state is set to *CLOSED* and credit memo is not created.
<article>



####  Requesting refund from Magento administration

To request a refund for a transaction from Magento administration, follow the steps given below.
1. Log in to your Magento administration panel.
2. In the menu, go to **Sales** > **Orders**. The order overview page is displayed.
3. Click the specific **order** you want to refund.
4. Click **Invoices** tab on **Order list View** navigation sidebar.
5. Go to **Invoice List Page** > **Order**, click **View** on invoice you need to request online refund.
6. Click **Credit Memo** on the top-right corner of the page.
7. In the **New Memo for Invoice** page, scroll down to the **Refund Totals** section.
8. In this section, you can request for refund online or offline.
    *   **Refund:** This option is used to request refund online to Midtrans. Midtrans automatically sends refund notification and changes the order status to **Closed**.
    *   **Refund Offline**: An offline refund does not trigger request refund to Midtrans. It is only refund in Magento side. You need to take action and carry out the refund manually from Midtrans dashboard. After a refund operation, the order status changes to **Closed**. This order status change is controlled by the Magento system.

The status change may not mean that the refund has carried out successfully on Midtrans side. When the refund is processed successfully, the transaction status in Midtrans dashboard changes to REFUND.

</article>
</details>

<details>
<summary>

### Transaction Test
</summary>
<article>
1. Perform successful transaction on your online store by entering the card details given below.

| Name        | Value               |
| :---------- | :------------------ |
| Card Number | 4811 1111 1111 1114 |
| CVV         | 123                 |
| Exp Month   | 01                  |
| Exp Year    | 2025                |
| OTP/3DS     | 112233              |

For more details, refer to [Testing Payments on Sandbox](/en/technical-reference/sandbox-test).
2. Examine a few points below to ensure plugin is installed and performs properly.

| Check Point                 | Error                                     | Troubleshooting                                              |
| --------------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| Order status in CMS backend | Order status not recorded in the backend. | Check endpoint/Payment Notification URL setting on MAP.<br> Check if your CMS/Notification URL is publicly accessible. |
| Merchant email notification | Notification not received.               | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications). |
| Customer email notification | Notification not received.                | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications). |

### Payment Example
![Magento 2 Payment Test](./../../asset/image/mag2-pay-show.gif)

</article>
</details>
<hr><br><br>

## PrestaShop
<hr>
Midtrans ❤️ PrestaShop! Integrate your PrestaShop store with Midtrans Snap payment gateway. Midtrans strives to make payments simple for you and the customers. This plugin will allow online payment on your PrestaShop store using various online payment channels.

### Requirements
Some of the requirements to continue with the integration process, are listed below.
* PrestaShop 1.6 and 1.7 or later | Tested up to v1.7
* PHP version 5.4 or later
* MySQL version 5.0 or later
* Midtrans plugin for PrestaShop [ [GitHub](https://github.com/veritrans/SNAP-Prestashop) | [Zip](https://github.com/veritrans/SNAP-Prestashop/archive/master.zip) ]

### Installing PrestaShop Plugin
To install the plugin, follow the steps given below.
1. Extract the plugin you have previously downloaded and rename folder as **midtranspay**. Then Zip the folder back into **midtranspay.zip**.
2. Go to **IMPROVE > Modules > Modules Manager** on PrestaShop administration page.
3. Click **Upload a module**.
4. Locate the **midtranspay.zip** file, click **Open**. A message to confirm the action is displayed.
5. Click **Configure**.
6. Find the **Midtrans Pay** module in the module manager and click **Configure**. Configure *Midtrans Pay* page is displayed.
   - Enter **Payment Option Display Text**. This text appears on the button displayed to the customer.
   - Select from **Environment** drop-down list. *Development* for testing transaction, *Production* for real transaction.
   - Enter **Merchant ID**.
   - Enter **Client key.**
   - Enter **Server key**.
   - Select desired order status for successful payments, from **Map payment SUCCESS status to** list.
   - Select desired order status for payment failure, from **Map payment FAILURE status to** list.
   - Select desired order status for challenge payment, from **Map payment PENDING/CHALLENGE status to** list.
     Other configurations are optional, you may leave it as is.

![Prestashop install midtrans](./../../asset/image/Prestashop-install.gif)

### Configuring PrestaShop Plugin Notification
To configure the PrestaShop plugin notification URL, follow the steps given below.
1. Login to your MAP account.
2. Select the **Environment** from drop-down list.
3. On the Home page, go to **SETTINGS > CONFIGURATION**.
   *Configuration* page is displayed.
4. Enter **Payment Notification URL**.
5. Enter **Finish Redirect URL**.
6. Enter **Error Redirect URL**.
7. Enter **Unfinish Redirect URL**
8. Click **Update**.
   A confirmation message is displayed.
   PrestaShop plugin notification is configured.

The table given below shows the fields and the redirect URL.

| Field                    | Redirect URL                                                 |
| ------------------------ | ------------------------------------------------------------ |
| Payment Notification URL | [your-site-url]/index.php?fc=module&module=midtranspay&controller=notification |
| Finish Redirect URL      | [your-site-url]/index.php?fc=module&module=midtranspay&controller=success |
| Error Redirect URL       | [your-site-url]/index.php?fc=module&module=midtranspay&controller=failure |
| Unfinish Redirect URL    | [your-site-url]/index.php?fc=module&module=midtranspay&controller=success |

?>***Note***: Please make sure to enter **http://** or **https://** in Notification URL and Redirect URL, according to your web-server configuration.<br>If you are not sure, open your web URL in a browser, and check the URL is **http** or **https** on the address bar.

<details>
<summary>

### Transaction Test
</summary>
<article>
1. Perform successful transaction on your online store by entering the card details given below.

| Name        | Value               |
| :---------- | :------------------ |
| Card Number | 4811 1111 1111 1114 |
| CVV         | 123                 |
| Exp Month   | 01                  |
| Exp Year    | 2025                |
| OTP/3DS     | 112233              |

For more details, refer to [Testing Payments on Sandbox](/en/technical-reference/sandbox-test).
2. Examine a few points below to ensure plugin is installed and performs properly.

| Check Point                 | Error                                     | Troubleshooting                                              |
| --------------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| Order status in CMS backend | Order status not recorded in the backend. | Check endpoint/Payment Notification URL setting on MAP.<br> Check if your CMS/Notification URL is publicly accessible. |
| Merchant email notification | Notification not received.                | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications). |
| Customer email notification | Notification not received.                | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications). |

### Payment Example
![Prestashop Payment Test](./../../asset/image/presta-pay-show.gif)

</article>
</details>
<hr><br><br>

## OpenCart
<hr>

Midtrans ❤️ OpenCart! This is official Midtrans extension for the OpenCart E-commerce platform.

### Requirements
Some of the requirements to continue with the integration process, are listed below.
* OpenCart minimal 2.0 or later | Tested up to v3.0
* PHP version 5.4 or later
* MySQL version 5.0 or later
* Midtrans plugin for OpenCart: For OpenCart v3.0 [[ GitHub](https://github.com/Midtrans/Midtrans-Opencart3) | [Zip](https://github.com/Midtrans/Midtrans-Opencart3/archive/master.zip) ]; For OpenCart v2.3 [ [GitHub](https://github.com/Midtrans/SNAP-Opencart-2.3/) | [Zip](https://github.com/Midtrans/SNAP-Opencart-2.3/archive/master.zip)]; For OpenCart v2.o, OpenCart v2.1, or OpenCart v2.2 [ [GitHub](https://github.com/veritrans/SNAP-Opencart) | [Zip](https://github.com/veritrans/SNAP-Opencart/archive/master.zip)]

### Installation of OpenCart plugin
To install OpenCart plugin, follow the steps given below.
1. Download midtrans OpenCart plugin and extract the zip file.
2. Locate the root OpenCart directory of your shop through FTP connection.
3. Copy the `admin`, `catalog`, and `system` folders into your OpenCart root folder, and merge it.
4. On your OpenCart administration page, go to **Extensions** > **Extensions**.
5. Select **Payment** Filter.
6. Select **Midtrans**.
7. Click **Install**.
OpenCart plugin is installed.


8. To configure merchant details, follow the steps given below.
    * Click **Edit**.
	 Configure Midtrans* page is displayed.
    * Click **Enable** in **Status**list 
    * Enter **Display name**. This text is displayed on button displayed to the customer.
    * Enter **Merchant ID** with your Merchant ID on [Midtrans account](https://dashboard.midtrans.com/settings/config_info/).
    * Select **Environment** dropdown list; *Sandbox* is for testing transaction, *Production* is for real transaction.
    * Enter **Client Key**.
    * Enter **Server Key**.

    ?> ***Note***: *Client Key* and *Server Key* for *Sandbox* environment and *Production* environment are different. For more details, refer to [Retrieve API Access Keys](/en/midtrans-account/overview.md#retrieving-api-access-keys).
    * Select **SUCCESS Order Status** drop-down list to select your desired order status when payment is successful. (recommended: `Processing`).
    * Select **PENDING Order Status** drop-down list to select your desired order status when payment is failure (recommended: `Pending`).
    * Select **FAILURE Order Status** drop-down list to select your desired order status when payment is pending (recommended: `Canceled`).

Other fields are optional, you can leave it as default.
![Opencart Install](./../../asset/image/Opencart-install.gif)

OpenCart plugin is installed.

### Configuring OpenCart Plugin Notifications
To configure the PrestaShop plugin notification URL, follow the steps given below.
1. Login to your MAP account.

2. Select the **Environment** from drop-down list.

3. On the Home page, go to **SETTINGS > CONFIGURATION**.
   *Configuration* page is displayed.
   
4. Enter **Payment Notification URL**.

5. Enter **Finish Redirect URL**.

6. Enter **Unfinish Redirect URL**.

7. Enter **Error Redirect URL**.

8. Click **Update**.
   A confirmation message is displayed.
   
   OpenCart plugin notification is configured.

The table given below shows the fields and the redirect URL.

<!-- tabs:start -->

#### **OpenCart v2.3 and 3**
| Label | Field | Redirect URL|
|----------|-------------|-------------|
| 1 | Payment Notification URL | http://[your shop's homepage]/index.php?route=extension/payment/snap/payment_notification |
| 2 | Finish Redirect URL | http://[your shop’s homepage]/index.php?route=extension/payment/snap/landing_redir& |
| 3 | Unfinish Redirect URL | http://[your shop’s homepage]/index.php?route=extension/payment/snap/landing_redir& |
| 4 | Error Redirect URL | http://[your shop’s homepage]/index.php?route=extension/payment/snap/landing_redir& |

#### **OpenCart v2, v2.1, v2.2**
| Label | Field | Redirect URL|
|----------|-------------|-------------|
| 1 | Payment Notification URL | http://[your shop's homepage]/index.php?route=payment/snap/payment_notification |
| 2 | Finish Redirect URL | http://[your shop’s homepage]/index.php?route=payment/snap/landing_redir& |
| 3 | Unfinish Redirect URL | http://[your shop’s homepage]/index.php?route=payment/snap/landing_redir& |
| 4 | Error Redirect URL | http://[your shop’s homepage]/index.php?route=payment/snap/landing_redir& |

<!-- tabs:end -->

?>***Note***: Please make sure to enter **http://** or **https://** in Notification URL and Redirect URL fields, according to your web-server configuration.<br>If you are not sure, open your website URL in a browser, and check the URL is **http** or **https** on the address bar.

<details>
<summary>

### Transaction Test
</summary>

<article>
1. Perform successful transaction on your online store by entering the card details given below.

| Name        | Value               |
| :---------- | :------------------ |
| Card Number | 4811 1111 1111 1114 |
| CVV         | 123                 |
| Exp Month   | 01                  |
| Exp Year    | 2025                |
| OTP/3DS     | 112233              |

For more details, refer to [Testing Payments on Sandbox](/en/technical-reference/sandbox-test).
2. Examine a few points below to ensure plugin is installed and performs properly.

| Check Point                 | Error                                     | Troubleshooting                                              |
| --------------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| Order status in CMS backend | Order status not recorded in the backend. | Check endpoint/Payment Notification URL setting on MAP.<br>Check if your CMS/Notification URL is publicly accessible. |
| Merchant email notification | Notification not received.                | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications). |
| Customer email notification | Notification not received.                | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications). |

### Payment Example

![Opencart Payment Test](./../../asset/image/opencart-pay-show.gif)

</article>
</details>
<hr><br><br>

## WHMCS
<hr>

### Requirements
Some of the requirements to continue with the integration process, are listed below.
   * WHMCS v5.3.12 - v7.x or later | Tested up to WHMCS v7.6
   * PHP version 5.4 or later
   * MySQL version 5.0 or later
   * Midtrans plugin for WHMCS [ [GitHub](https://github.com/veritrans/SNAP-whmcs) | [Zip](https://github.com/veritrans/SNAP-whmcs/archive/master.zip) ]

### Installing WHMCS plugin
To install WHMCS plugin, follow the steps given below.
1. Download the modules from the link above.
2. Extract **Whmcs-master.zip** file you have previously downloaded.
3. Upload and merge module folder that you have extracted into your WHMCS directory, **Installation and Configuration**.
4. Access your WHMCS administration page.
5. Go to **Setup** > **Payments** >**Payment Gateways**.
6. Click **Midtrans** payment method.
 *Configuration* page is displayed.
7. Perform the following actions on *Configuration* page.
   * Enter **Display Name**.
   * Enter **Midtrans Client Key**.
   * Enter **Midtrans Server Key**.
   * For *Production* environment, select the **Production Mode** check box. For *Sandbox* environment, click to clear the **Production Mode** check box.
   * Click **Save Changes**.
The WHMCS plugin is installed successfully.
![WHMCS](./../../asset/image/snap-whmcs1.png)

### Configuring WHMCS Plugin Notification
To configure the WHMCS plugin notification URL, follow the steps given below.
1. Login to your MAP account.
2. Select the **Environment** from drop-down list.
3. On the Home page, go to **SETTINGS > CONFIGURATION**.
   *Configuration* page is displayed.
4. Enter **Payment Notification URL**.
5. Enter **Finish Redirect URL**.
6. Enter **Unfinish Redirect URL**.
7. Enter **Error Redirect URL**.
8. Click **Update**.
   A confirmation message is displayed.
   WHMCS plugin notification is configured.

The table given below shows the fields and the redirect URL.

| Label | URL Role | Redirect URL|
|----------|-------------|-------------|
| 1 | Payment Notification URL | [your-site-url]/modules/gateways/callback/veritrans.php |
| 2 | Finish Redirect URL | [your-site-url] |
| 3 | Unfinish Redirect URL | [your-site-url] |
| 4 | Error Redirect URL | [your-site-url] |

?>***Note***: Enter **http://** or **https://** in *Notification URL* and *Redirect URL*, according to your web-server configuration.
If you are not sure, open your website URL in a browser, and check the URL is **http** or **https** on the address bar.

<details>
<summary>

### Transaction Test
</summary>

<article>
1. Perform successful transaction on your online store by entering the card details given below.

| Name        | Value               |
| :---------- | :------------------ |
| Card Number | 4811 1111 1111 1114 |
| CVV         | 123                 |
| Exp Month   | 01                  |
| Exp Year    | 2025                |
| OTP/3DS     | 112233              |

For more details, refer to [Testing Payments on Sandbox](/en/technical-reference/sandbox-test).
2. Examine a few points below to ensure plugin is installed and performs properly.

| Check Point                 | Error                                     | Troubleshooting                                              |
| --------------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| Order status in CMS backend | Order status not recorded in the backend. | Check endpoint/Payment Notification URL setting on MAP.<br> Check if your CMS/Notification URL is publicly accessible. |
| Merchant email notification | Notification not received.                | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications). |
| Customer email notification | Notification not received.                | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications). |

</article>
</details>
<hr><br><br>

## Drupal 8
<hr>

Midtrans ❤️ Drupal 8! This is the official Midtrans extension for the Drupal E-commerce platform. You can easily integrate your Drupal commerce store with Midtrans payment gateway.

### Requirements
Some of the requirements to continue with the integration process, are listed below.
 * Drupal v8.x | Tested up to v8.x
 * Drupal Commerce 8.x-2.xx | Tested up to v8.x - 2.x
 * PHP v5.6.x or later
 * MySQL version 5.0 or later
 * Midtrans plugin for Drupal [ [GitHub](https://github.com/Midtrans/Midtrans-Drupal8) | [Zip](https://github.com/Midtrans/Midtrans-Drupal8/archive/master.zip) ]

### Installing Drupal 8 Plugin
To install Drupal 8 plugin, follow the steps given below.
1. Download the plugin file and unzip it, rename folder to **commerce_midtrans**.
2. Using a FTP client, or your hosting control panel, upload the unzipped plugin folder to your Drupal modules installation's **[Drupal folder]/modules/contrib/** directory.
3. Open Drupal administration page, click **Extend**.
4. Under **COMMERCE (CONTRIB)** group, click **Commerce Midtrans**
    ![Drupal 8 1](./../../asset/image/drupal8_1.png)
5. Click **Install**.
Drupal 8 plugin is installed.

### Configuring Drupal 8 Plugin
1. Go to **Commerce** > **Configuration** > **Payment** > **Payment gateways**.
![Drupal 8 2](./../../asset/image/drupal8_2.png)
2. Click **Add payment gateway**.
![Drupal 8 3](./../../asset/image/drupal8_3.png)
**Add payment gateway page** is displayed.
3. Perform the following actions on *Payment gateways* page.

   - Enter **Name**. This text appears on the button displayed to the customer.

   - Select **Plugins** radio button.

   - Select **Mode**; *Sandbox* for testing transaction and *Production* for real transaction.

   - Enter **Merchant ID**.

   - Enter **Server key**.

   - Enter **Client key**.

 ?>***Note***: You may get *Merchant ID, Server key,* and *Client key* on Midtrans MAP Dashboard.

Other fields are optional, you may leave it as is.
4. Click **Save**.
   A confirmation message is displayed.
Drupal 8 plugin is configured.
![Drupal 8 4](./../../asset/image/drupal8_4.png)

### Configuring Drupal Notifications
To configure the Drupal plugin notification URL, follow the steps given below.
1. Login to your MAP account.
2. Select the **Environment** from drop-down list.
3. On the Home page, go to **SETTINGS > CONFIGURATION**.
   *Configuration* page is displayed.
4. Enter **Payment Notification URL**.
5. Enter **Finish Redirect URL**.
6. Enter **Unfinish Redirect URL**.
7. Enter **Error Redirect URL**.
8. Click **Update**.
   A confirmation message is displayed.

Drupal plugin notification is configured.


The table given below shows the fields and the redirect URL.

| Label | URL Role                 | Redirect URL                            |
| ----- | ------------------------ | --------------------------------------- |
| 1     | Payment Notification URL | [your-site-url]/payment/notify/midtrans |
| 2     | Finish Redirect URL      | [your-site-url]                         |
| 3     | Unfinish Redirect URL    | [your-site-url]                         |
| 4     | Error Redirect URL       | [your-site-url]                         |

?>***Note***: Enter **http://** or **https://** in *Notification URL* and *Redirect URL*, according to your web-server configuration.<br>If you are not sure, open your website URL in a browser, and check the URL is **http** or **https** on the address bar.

<details>
<summary>

### Transaction Test
</summary>
<article>
1. Perform successful transaction on your online store by entering the card details given below.

| Name        | Value               |
| :---------- | :------------------ |
| Card Number | 4811 1111 1111 1114 |
| CVV         | 123                 |
| Exp Month   | 01                  |
| Exp Year    | 2025                |
| OTP/3DS     | 112233              |

For more details, refer to [Testing Payments on Sandbox](/en/technical-reference/sandbox-test).
2. Examine a few points below to ensure plugin is installed and performs properly.

| Check Point                 | Error                                     | Troubleshooting                                              |
| --------------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| Order status in CMS backend | Order status not recorded in the backend. | Check endpoint/Payment Notification URL setting on MAP.<br> Check if your CMS/Notification URL is publicly accessible. |
| Merchant email notification | Notification not received.                | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications). |
| Customer email notification | Notification not received.                | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications). |

### Payment Example
![Drupal Payment Test](./../../asset/image/drupal8-pay-show.gif)

</article>
</details>
<hr><br><br>

## WordPress - Easy Digital Download
<hr>

Midtrans ❤️ EDD! Integrate your Easy Digital Download (EDD) store with Midtrans Snap payment gateway. Midtrans strives to make payments simple for both the merchant and the customers. This plugin will allow online payments on your EDD store using various online payment channels.

Midtrans EDD plugins also available on [WordPress plugins store](https://wordpress.org/plugins/edd-midtrans-gateway/).

### Requirements
Some of the requirements to continue with the integration process, are listed below.
   * WordPress 3.9.1 or later | Tested up to v5.x
   * Easy Digital Downloads 2.0 or later | Tested up to v2.x
   * PHP version 5.4 or later
   * MySQL version 5.0 or later
   * PHP CURL enabled server/host
   * Midtrans plugin for WordPress EDD [ [GitHub](https://github.com/Midtrans/midtrans-edd) | [Zip](https://github.com/Midtrans/midtrans-edd/archive/master.zip) ]

### Installing WordPress EDD Plugin
To install WordPress EDD plugin, select any **one** of the installation methods given below.

#### **Simple Installation**

To install WordPress EDD plugin, follow the steps given below.
1. Login to your WordPress administration panel.
2. Go to **Plugins** > **Add New**.
3. Enter **Midtrans-Easy-Digital-Downloads** in the search bar.
4. Click **Install Now**.
5. Click **Activate**.
 Proceed to configuration section.
![EDD Install](./../../asset/image/Edd-Install.gif)

#### **Manual Installation**

The manual installation method involves downloading feature-rich plugin and uploading it to your Webserver through your favorite FTP application. To install WordPress EDD manually, follow the steps given below.
1. Download the plugin file to your computer and unzip it.
2. Extract the plugin, then rename the folder modules as **edd-midtrans-gateway**
3. Using an FTP program, or your hosting control panel, upload the unzipped plugin folder to your WordPress installation wp-content/plugins/ directory.
4. Install and Activate the plugin from the **Plugins** menu on the WordPress administration panel.
5. Activate Easy Digital Downloads - Midtrans Gateway plugin from **Plugin** menu in your WordPress administration page.

### Configuring EDD Plugin
To configure EDD plugin, follow the steps given below.
1. On Dashboard, go to **Downloads(1) > Settings(2)**.
 *Easy Digital Downloads Settings* page is displayed.
2. Select **Payment Gateways(3)** tab.
3. Select **General**.
4. For *Sandbox* environment, select the **Test mode** check box. For *Production* environment, click to clear the **Test mode** check box.
5. Under **Payment Gateways**, click **Midtrans (4)**.
6. In the **Default Gateway(5)** list, click **Midtrans**.
7. Click **Save Changes(6)**.
    ![Edd Config 1](./../../asset/image/EDD-Config-1.png)
8. Click **Midtrans(7)**.
9. Perform the following actions on *Midtrans Settings* page.
    - Enter **Checkout Label**.
    - Enter **Merchant ID**.
    - For *Production* Environment, enter **Production Server Key** and **Production Client Key**. For *Sandbox* Environment, enter **Sandbox Server Key** and **Sandbox Client Key**.
10. Click **Save Changes**.

Midtrans payment setting is configured.
![Edd Config 2](./../../asset/image/EDD-Config-2.png)

### Configuring EDD Notifications
To configure the EDD plugin Notification URL, follow the steps given below.
1. Login to your MAP account.
2. Select the **Environment** from drop-down list.
3. On the Home page, go to **SETTINGS > CONFIGURATION**.
   *Configuration* page is displayed.
4. Enter **Payment Notification URL**.
5. Enter **Finish Redirect URL**.
6. Enter **Unfinish Redirect URL**.
7. Enter **Error Redirect URL**.
8. Click **Update**.
   A confirmation message is displayed.
   EDD plugin notification is configured.



The table given below shows the fields and the redirect URL.

| Label | URL Role                 | Redirect URL                           |
| ----- | ------------------------ | -------------------------------------- |
| 1     | Payment Notification URL | [your-site-url]/?edd-listener=midtrans |
| 2     | Finish Redirect URL      | [your-site-url]                        |
| 3     | Unfinish Redirect URL    | [your-site-url]                        |
| 4     | Error Redirect URL       | [your-site-url]                        |

?> ***Note***: Enter **http://** or **https://** in *Notification URL* and *Redirect URL*, according to your web-server configuration.
<br>If you are not sure, open your website URL in a browser, and check the URL is **http** or **https** on the address bar.

<details>
<summary>

### Transaction Test
</summary>
<article>
1. Perform successful transaction on your online store by entering the card details given below.

| Name        | Value               |
| :---------- | :------------------ |
| Card Number | 4811 1111 1111 1114 |
| CVV         | 123                 |
| Exp Month   | 01                  |
| Exp Year    | 2025                |
| OTP/3DS     | 112233              |

For more details, refer to [Testing Payments on Sandbox](/en/technical-reference/sandbox-test).
2. Examine a few points below to ensure plugin is installed and performs properly.

| Check Point                 | Error                                     | Troubleshooting                                              |
| --------------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| Order status in CMS backend | Order status not recorded in the backend. | Check endpoint/Payment Notification URL setting on MAP.<br> Check if your CMS/Notification URL is publicly accessible. |
| Merchant email notification | Notification not received.                | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications). |
| Customer email notification | Notification not received.                | Check Email Notifications settings on MAP. For more details, refer to [Configuring Email Notifications](/en/after-payment/dashboard-usage.md#configuring-email-notifications). |

### Payment Example
![EDD Payment Test](./../../asset/image/edd-show-pay.gif)

</article>
</details>