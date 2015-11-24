Cookies-Phonegap-Plugin
=======================

Phonegap Plugin that enables you to clear all cookies stored on webview.  

## Why need to use Cookies Plugin?
In phonegap, contents (html/css/js files) are loaded from local resources with `file://` protocol and when `document.cookie` is called, it returns an empty string. Phonegap handles cookies internally and stores on the browser within the application. Therefore, this plugin is required to clear internal cookies stored on the webview. 

!! Please be careful, this plugin will clear all session, expired and other cookies whenever it's invoked.

## Installation

You can simply add this plugin to your code base either using cordova-plugman or manually.

If you use command line interface (CLI), you can use the following link: 

```
$ phonegap local plugin add https://github.com/kinsights/Phonegap-Cookies-Plugin.git
```
If you add this plugin manually, 
 + Add native files within `src/` folder to your project.
 + Then, add `cookies.js` source within `www/` folder to your project.
 + Finally, edit your `cordova_plugins.js` file and add the following code block.
```javascript 
 {
        "file": "plugins/com.kinsights.Cookies/www/cookies.js",
        "id": "com.kinsights.Cookies",
        "clobbers": [
            "window.cookies"
        ]
 }
```
 `file` stands for javascript file path stored in your project.
 `id` stands for native code file path stored in your project.
 + Add a new dependency for your plugin in `config.xml`
 
 ```
     <?xml version='1.0' encoding='utf-8'?>
       <!-- If your platform is iOS, add the following feature tag only -->
       <feature name="Cookies">
          <param name="ios-package" value="CDVCookies" />
       </feature>
       
       <!-- If your platform is Android, add the following feature tag only -->
       <feature name="Cookies" >
          <param
             name="android-package"
             value="com.kinsights.Cookies" />
       </feature>
     </xml>
  ``` 

 + Done!

## Usage
You can call directly `window.cookies.clear()` function on your JavaScript code. Also, you are capable of adding success and fail callback function parameters.

Sample Code :

```javascript
window.cookies.clear(function successCallback() {
   console.log('successfully completed!!');
}, function failCallback(){
   // note: fail callback is optional 
   console.log('failed!!');  
});
```
