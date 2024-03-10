# A. Config URL Rewrite
## I. Check OS architecture
Open cmd
```
wmic os get osarchitecture
```
## II. Install IIS URL Rewrite Module
<ul>
  <li>Google url rewrite download</li>
  <li>1st link: https://www.iis.net/downloads/microsoft/url-rewrite</li>
  <li>Download URL Rewrite Module</li>
  <li>Click on x64 installer</li>
  <li>Install the file on server</li>
  <li>Restart IIS manager ( close and reopen)</li>
  <li>Restart the Website</li>
</ul>
 







# B. IIS
## I. Add Website
Site name, Physical path, ip, port, host name
## II. Application Pools
Right click mySite --> Basic Settings
Under .NET CLR version: No Managed Code
Angular does not need .NET framework run on the background, remove this will improve performance

# C. Angular Project
## I. File angular.json
Under projects --> mySite --> architect --> build --> options --> assets <br>
add "src/web.config"



## II. File web.config
```
<?xml version="1.0" encoding="utf-8"?>
<configuration>

<system.webServer>
  <rewrite>
    <rules>
      <rule name="Angular Routes" stopProcessing="true">
        <match url=".*" />
        <conditions logicalGrouping="MatchAll">
          <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
          <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
        </conditions>
        <action type="Rewrite" url="/" />
      </rule>
    </rules>
  </rewrite>
</system.webServer>

</configuration>
```

## III. Build the project
```
ng build
```
Warning: bundle initial exceeded maximum budget. Budget 500.00 kB was not met by 411.28 kB with a total of 911.28 kB.
Budget Info:
```
What is the budget used for?
Size Limit: The budget sets a maximum size limit for the generated JavaScript bundle files. It helps enforce constraints on the size of your application's assets, which can impact performance, load times, and user experience.

Optimization: By setting a budget, you're encouraged to optimize your Angular application to keep its size manageable. This can involve techniques like code splitting, lazy loading, tree shaking, and minification to reduce the size of the generated bundle files.

Pros and Cons of Increasing the Budget:
Pros:
Flexibility: Increasing the budget provides more flexibility in terms of the size of your application's assets. You may need to increase the budget if your application's codebase grows significantly or if you're integrating third-party libraries that contribute to the bundle size.

Avoid False Positives: Sometimes, the warning about exceeding the budget may be triggered by legitimate reasons, such as including necessary functionality or libraries in your application. Increasing the budget can help avoid false positives and allow your application to build successfully.

Cons:
Performance Impact: Larger bundle sizes can lead to slower load times, especially on slower network connections or devices with limited resources. Users may experience delays when accessing your application, impacting the overall user experience.

Network Bandwidth: Larger bundle sizes require more network bandwidth to download, which can be a concern for users on limited data plans or in regions with poor internet connectivity. It's important to consider the impact on users' data usage and accessibility.

Caching: Larger bundle sizes may affect caching strategies, as browsers may need to download and cache larger files, potentially leading to increased cache misses and slower subsequent page loads.

Conclusion:
While increasing the budget may solve immediate build issues, it's essential to consider the long-term implications on performance, user experience, and accessibility. Striking a balance between functionality and optimization is key. Continuously monitor and optimize your application's bundle size to ensure it remains within acceptable limits while delivering a fast and responsive user experience.


```
Increase Budget:
File angular.json
Project --> mySite --> architect --> build --> configurations --> production --> budgets
Change
```
{
  "type": "initial",
  "maximumWarning": "500kb",
  "maximumError": "1mb"
},
```
To
```
{
  "type": "initial",
  "maximumWarning": "1mb",
  "maximumError": "2mb"
},
```






