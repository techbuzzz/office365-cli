# spo app retract

Retracts the specified app from the tenant app catalog

## Usage

```sh
spo app retract [options]
```

## Options

Option|Description
------|-----------
`--help`|output usage information
`-i, --id <id>`|ID of the app to retract. Needs to be available in the tenant app catalog.
`-u, --appCatalogUrl [appCatalogUrl]`|(optional) URL of the tenant app catalog site. If not specified, the CLI will try to resolve it automatically
`--confirm`|Don't prompt for confirming retracting the app from the tenant app catalog
`-o, --output [output]`|Output type. `json|text`. Default `text`
`--verbose`|Runs command with verbose logging
`--debug`|Runs command with debug logging

!!! important
    Before using this command, log in to a SharePoint Online site, using the [spo login](../login.md) command.

## Remarks

To retract an app from the tenant app catalog, you have to first log in to a SharePoint site using the [spo login](../login.md) command, eg. `spo login https://contoso.sharepoint.com`.

If you don't specify the URL of the tenant app catalog site using the **appCatalogUrl** option, the CLI will try to determine its URL automatically. This will be done using SharePoint Search. If the tenant app catalog site hasn't been crawled yet, the CLI will not find it and will prompt you to provide the URL yourself.

If the app with the specified ID doesn't exist in the tenant app catalog, the command will fail with an error.

## Examples

Retract the specified app from the tenant app catalog. Try to resolve the URL of the tenant app catalog automatically. Additionally, will prompt for confirmation before actually retracting the app.

```sh
spo app retract -i 058140e3-0e37-44fc-a1d3-79c487d371a3
```

Retract the specified app from the tenant app catalog located at _https://contoso.sharepoint.com/sites/apps_. Additionally, will prompt for confirmation before actually retracting the app.

```sh
spo app retract -i 058140e3-0e37-44fc-a1d3-79c487d371a3 -u https://contoso.sharepoint.com/sites/apps
```

Retract the specified app from the tenant app catalog. Try to resolve the URL of the tenant app catalog automatically. Will not prompt for confirmation before retracting the app.

```sh
spo app retract -i 058140e3-0e37-44fc-a1d3-79c487d371a3 --confirm
```

## More information

- Application Lifecycle Management (ALM) APIs: [https://docs.microsoft.com/en-us/sharepoint/dev/apis/alm-api-for-spfx-add-ins](https://docs.microsoft.com/en-us/sharepoint/dev/apis/alm-api-for-spfx-add-ins)