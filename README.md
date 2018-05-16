# Game Applet Loader

GAL for short, is a simple Java program that loads Java Applets and shows them in a barebones GUI.

GAL will automatically notify you of updates and ask if you'd like to open the download link in the browser, but this can be suppressed in `config.json` by setting `skip_updates` to `true`.

You can also load custom Look and Feel themes, by setting `look_and_feel`to the appropriate fully qualified Class name of the Look and Feel you'd like to use.

### Features

- Support resizeable applets

- Multiple concurrent applets

- Loading applets from the local file system, which eliminates initial loading time

### Limitations

- Does not presently cache remote Applets - May add in the future

- There is no scripting/reflection support, this was removed from the original version, as I consider it to be too tempting for cheaters/hackers

- There is not presently an any option to enable multiple logins on the same server, you can circumvent this by unlocking and deleting `C:/.jagex_cache_32/random.dat`, or your system's equivalent, before loading an Applet

&nbsp;

### Profiles

Profiles are defined in a simple JSON file located in each profile's folder.

**The format is as follows:**

- `main_class` - The Applet class to be loaded
- `uri` - The URI, or path, of the Jar/Class file to be loaded; can be either remote or local
- `codebase` - The codebase that the Applet will consider itself to be running from
- `width`- The width of the Applet
- `height` - The height of the Applet
- `parameters` - a JSON Object containing the Applet parameters

### Example Profile settings

A working example of a remotely loaded Applet:

```
{
   "main_class":"ArcanistsMulti",
   "uri":"http://arcanists14.funorb.com/g=arcanistsmulti/arcanistsmulti/8132/client_-859383175.jar",
   "script_folder":"scripts",
   "codebase":"http://arcanists14.funorb.com/g=arcanistsmulti/arcanistsmulti/8132/",
   "width":640,
   "height":480,
   "parameters":{
      "modewhat":0,
      "servernum":8132,
      "gamecrc":911646149,
      "gameport1":43594,
      "gameport2":443,
      "instanceid":0,
      "member":"no",
      "overxgames":45,
      "overxachievements":1000,
      "currency":2,
      "cookieprefix":"",
      "cookiehost":".funorb.com"
   }
}
```

This example uses a remote URI, this means that there will be an initial waiting period while GAL loads the Applet remotely. There is presently no loading screen, so GAL will simply appear to hang for a time. There will be no additional loading time, if the same Applet is loaded in another window, before closing GAL.

Typically, it is preferred to load Applets locally, from the same folder that the Profile's `settings.json` file is located, as this will effectively eliminate loading times.
