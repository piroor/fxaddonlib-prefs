# Preferences Library

## Usage

Developer-friendly utility (for bootstrapped extensions):

    // you can create a new "store" which is bound to specific base key (domain).
    var store = window['piro.sakura.ne.jp'].prefs.createStore('extensions.someextension');
    
    // you can define new preference under the base key.
    store.define('enabled' /* property name and key */,
                 true      /* default value */);
    // then it will be defined as: extensions.someextension.enabled=true
    // and you can read the value as a static property like:
    var enabled = store.enabled;
    // the value will be updated automatically when the user change the preference.
    
    // if you want to define the preference with a key different to the property name...
    store.define('leftMargin', true, 'margin.left' /* the actual key */);
    
    // after all, free the memory.
    store.destroy();

Low level APIs (for legacy type addons):

    var value = window['piro.sakura.ne.jp'].prefs.getPref('my.extension.pref');
    window['piro.sakura.ne.jp'].prefs.setPref('my.extension.pref', true);
    window['piro.sakura.ne.jp'].prefs.clearPref('my.extension.pref');
    
    var listener = {
          domains : [
            'browser.tabs',
            'extensions.someextension'
          ],
          observe : function(aSubject, aTopic, aData)
          {
            if (aTopic != 'nsPref:changed') return;
            var value = window['piro.sakura.ne.jp'].prefs.getPref(aData);
          }
        };
    window['piro.sakura.ne.jp'].prefs.addPrefListener(listener);
    window['piro.sakura.ne.jp'].prefs.removePrefListener(listener);
