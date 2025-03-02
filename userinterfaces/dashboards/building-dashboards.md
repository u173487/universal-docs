---
description: Dashboards are the root component for your web page.
---

# Dashboards

Dashboards can contain one or more pages. The simplest dashboard will contain a single page with some content. You can call any PowerShell cmdlet that is available on your machine to populate your dashboard.

Here's an example of simple dashboard that displays some text.

```powershell
New-UDDashboard -Title 'My New Dashboard' -Content {
    New-UDTypography -Text 'Hello!'
}
```

## New-UDDashboard

The top-level cmdlet for dashboards is `New-UDDashboard`. You need to call it when returning a dashboard. You can use it with or without pages.&#x20;

### Content

The content of the dashboard is a series of components to display on the page. It's a script block that will return all the components in the order they will be rendered on the page. You can use the Grid component to layout items and display things like text with typography.&#x20;

```powershell
New-UDDashboard -Title 'My New Dashboard' -Content {
    New-UDTypography -Text 'Hello!'
}
```

### Header Customization

You can customize the header of the dashboard using several parameters.&#x20;

To change the navigation layout, use the `-Navigation` and `-NavigationLayout` parameters.

```powershell
New-UDDashboard -Content {
} -Navigation (
    New-UDList -Children {
        New-UDListItem -Label "Home"
        New-UDListItem -Label "Getting Started" -Children {
            New-UDListItem -Label "Installation" -OnClick {}
            New-UDListItem -Label "Usage" -OnClick {}
            New-UDListItem -Label "FAQs" -OnClick {}
            New-UDListItem -Label "System Requirements" -OnClick {}
            New-UDListItem -Label "Purchasing" -OnClick {}
        }
    }
) -NavigationLayout permanent
```

## Components

Components are the individual widgets that you can place on you dashboard. There are components for displaying data, taking user input, adding text and images and more. Components can be downloaded as PowerShell modules and added to your dashboard.

Components are be caused using the standard verb-name syntax for any PowerShell cmdlet.

```powershell
New-UDPage -Content {
    New-UDTextbox
}
```

Learn more about [components here](building-dashboards.md#components).

## Pages

You can specify multiple pages within a dashboard. Each page defines a route. As for v3, all pages are dynamic. PowerShell will execute on each page load to render the new page. Since UD is a single page application, the web browser does not need to refresh the entire web page when navigating between the different dashboard pages.

```powershell
$Pages = @()
$Pages += New-UDPage -Name 'My Home Page' -Content {}
$Pages += New-UDPage -Name 'Diagnostics' -Content {}
New-UDDashboard -Pages $Pages -Title 'Dashboard'
```

Learn more about [Pages here](building-dashboards.md#pages).&#x20;

## Built-in Variables

Built-in variables can be found on the [variables page](../../platform/variables.md#dashboards).

## Debugging

{% hint style="info" %}
You can also use the [Debugging Tools](../../development/debugging-scripts.md#integrated-debugger) with dashboards.
{% endhint %}

When building a dashboard, you will likely run into issues with cmdlet calls or syntax. Dashboards will auto reload as you make changes to the dashboard files. If a dashboard fails to start, you can navigate to the admin page, click Dashboards and click the Info button next to your dashboard.

The Log tab will show all the logging coming from the PowerShell execution from within in your dashboard. This should allow you to easily see errors and warnings coming from your dashboard.

You can use `Write-Debug` to add additional log messages to your dashboard. To enable debug logging, you will have to set the `$DebugPreference` variable at the top of your dashboard script.

```powershell
$DebugPreference = 'Continue'
```

## Menu

You can customize the dashboard menu by using the `-Menu` parameter.&#x20;

```powershell
New-UDDashboard -Title 'Dashboard' -Content {

} -Menu {
    New-UDMenuItem -Text 'Profile' -OnClick {
        Show-UDModal -Content {
            New-UDTypography -Text 'Welcome to your profile!'
        }
    }
}
```
