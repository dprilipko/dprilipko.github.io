#### Apple App Site Association file

This file should be in the root of the site, with name `apple-app-site-association` without extension.
Content inside:
```
{
    "applinks": {
        "apps": [],
        "details": [
            {
                "appID": "JZUX7Z6U42.de.clapp.handelsblatt.One-dev",
                "paths": [
                    "/cmsid/*"
                ]
            }
        ]
    }
}
```
where:
1) The value for the `apps` key must be present and must be an empty array.
2) The `appID` taken from Member Center (in form of `{Team ID}.{Bundle ID}`).
3) `paths` defines the urls in which iOS will open an application with the specified appID instead of the site.

For `paths`, there are special characters in the markup:

* If the application supports all sections of the site, simply use `*`
* Specify link by writing `/news/latest/`
* You can specify a section using `*` as a symbol that represents any substring.
 For example `/*/latest/` or `/videos/*` .
* For substituting any one character `?` . Example: `/videos/201?/`

**Note that paths are case sensitive.**

A few subtleties. The task is as follows: you need to open the video (`/videos/cats/video1`) in the application, but do not open sections (`/videos/cats`). 
In the apple-app-site-association file, write the following path:

`/videos/*/*/`

note the closing slash, without it the paths of the format `/videos/2014` will still open in the application.
