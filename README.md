# Preferences Library

## Usage

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

