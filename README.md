*This project is a billing provider plugin to [android-store](https://github.com/soomla/android-store).*


## android-store-bazaar

android-store-bazaar is the default billing service plugin for android-store. It uses the default code given by Bazaar which was adapted to IabHelper and IIabService interface so it'll be useful to SOOMLA's android-store.


## Getting Started

In order to work with this plugin you first need to go over android-store's [Getting Started](https://github.com/soomla/android-store#getting-started).

The steps to integrate this billing service are also in android-store's [Selecting Billing Service](https://github.com/soomla/android-store#bazaar) but we will also write them here for convenience:


1. Add `AndroidStoreBazaar.jar` from the `build` folder to your project.
2. Make the following changes in AndroidManifest.xml:

  Add the following permission (for Bazaar):

  ```xml
    <uses-permission android:name="com.android.vending.BILLING" />
  ```

  Add the IabActivity to your `application` element, the plugin will spawn a transparent activity to make purchases. Also, you need to tell us what plugin you're using so add a meta-data tag for that:

  ```xml
    <activity android:name="com.soomla.store.billing.bazaar.BazaarIabService$IabActivity"
      android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen"/>
    <meta-data android:name="billing.service" android:value="bazaar.BazaarIabService" />
  ```

3. After you initialize `SoomlaStore`, let the plugin know your public key from the dev console:

  ```Java
    BazaarIabService.getInstance().setPublicKey("[YOUR PUBLIC KEY FROM THE MARKET]");
  ```


4. If you want to allow the test purchases, all you need to do is tell that to the plugin:

  ```Java
    BazaarIabService.AllowAndroidTestPurchases = true;
  ```

For Bazaar, We recommend that you open the IAB Service and keep it open in the background in cases where you have an in-game storefront. This is how you do that:

  When you open the store, call:  

  ```Java
    SoomlaStore.getInstance().startIabServiceInBg();
  ```

  When the store is closed, call:  

  ```Java
    SoomlaStore.getInstance().stopIabServiceInBg();
  ```


## Contribution


We want you!

Fork -> Clone -> Implement -> Test -> Pull-Request. We have great RESPECT for contributors.

## SOOMLA, Elsewhere ...


+ [Framework Page](http://project.soom.la/)
+ [On Facebook](https://www.facebook.com/pages/The-SOOMLA-Project/389643294427376)
+ [On AngelList](https://angel.co/the-soomla-project)

## License

MIT License. Copyright (c) 2014 SOOMLA. http://soom.la
+ http://www.opensource.org/licenses/MIT
