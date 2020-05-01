# Google-Sankey
Adds Google sankey chart to UniversalDashboard based on https://www.npmjs.com/package/react-google-charts

## First-Off
I kind of broke the rules on this component....I know the standard naming convension, and well I did apply it, then a fellow
dashboard user reminded me that the Sankey chart was part of Nivo charts. I felt real bad. I was lucky enough to get permission
to use this **but please if you are using the community version go buy the enterprise version it is certainly worth the money
and will help the developer keep developing this amazing module**

## New-GoogleSankey
Yep that is the name of this command that's how I feel I broke the rule book on this one.

## Parameters
Tried to keep this super simple, so there are only 3 parameters which are all pretty straight-forward:-
* **-Width** This is a string value to set the **width** of the Sankey chart, this is defaulted to "500px"
* **-Height** This is a string value to set the **height** of the Sankey chart, this is defaulted to "500px"
* **-Data** This is a **3 dimensional multi array that has to contain a heading** please see example below

## Covid Times
Well being the semi-morbid person I am what better chart results can you get than using offcial covid19 figures released. It seemed
a good idea at the time anyway for proof of concept.  So I Googled some figures and locations and then did this chart from those
results I found...Ideally I was looking to try and find a site that would show me the spread of covid but could only find figures.

## Example Dashboard using this new component New-GoogleSankey

```
Import-Module -Name UniversalDashboard
Import-Module -Name UniversalDashboard.GoogleSankey
Get-UDDashboard | Stop-UDDashboard
Start-UDDashboard -Port 10005 -Dashboard (
    New-UDDashboard -Title "Powershell UniversalDashboard" -Content {
        $MultiArray = @()
        # MAKE SURE YOU GIVE THE ARRAY A HEADING TO COVER THE 3 DIMENSIONAL ARRAY YOU ARE PASSING IT
        $MultiArray += , @('From', 'To', 'Value' )
        $MultiArray += , @('London', 'Scotland', 6067)
        $MultiArray += , @('London', 'North West', 11368)
        $MultiArray += , @('Yorkshire', 'North West', 10027)
        $MultiArray += , @('South East', 'Yorkshire', 9070)
        $MultiArray += , @('London', 'South East', 8517)
        $MultiArray += , @('London', 'East England', 6002)
        $MultiArray += , @('Wales', 'Yorkshire', 18000)
        $MultiArray += , @('Midlands', 'Wales', 5610)
        $MultiArray += , @('Midlands', 'South East', 3392)

        New-GoogleSankey -Id "SANKEYCHART" -data @($MultiArray) -Width "600px" -Height "600px"
    }
)

```

 So there you have it an example using all 3 parameters
