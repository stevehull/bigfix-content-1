## Dashboards / Wizards meant to be used in the BigFix console.

**What is a Dashboard?**

**What is a Wizard?**

**How are they different than a Custom Web Report?**

- They are all basically the exact same thing. The main difference is that a Wizard is expected to have multiple "Pages" and "Steps" that are separate HTML documents internally. Dashboards and Custom Web Reports are expected to be a single HTML document, but through use of JavaScript, that single HTML document could have a wizard within it, or some other method for emulating multiple "Steps", though it could also be anything else.
- a Custom Web Report is within a WebReports context, while Dashboards & Wizards are within a slightly different BigFix Console context. This means there are a few things that work in one and not the other.

**How are all of the above different than a Client UI Dashboard?**

- The most significant difference about a Client UI Dashboard vs the others is that the Client UI Dashboard can only work with the single computer that it is running on, and cannot use Session Relevance. While the others (Dashboard/Wizard/WebReport) can provide summary results from multiple computers, they don't have to, which means if you have one that displays data from a single computer, then it is nearly identical to a Client UI Dashboard. The real power of Dashboards/Wizards/WebReports is that they can work with results across multiple computers, so using them for a single computer is a very simplified use case, but that doesn't change the fact that you could have a single unified view of a single computer across all of them, including a Client UI Dashboard.
- In order for this to really be the same, the Dashboard or WebReport would have to provide a way to pick a single computer to view the data, while the Client UI Dashboard would only work with the computer it is on.
- The other part that is needed is that the Client UI Dashboard would be powered by **client relevance** while the Dashboard or WebReport would have to rely on **Session Relevance Properties** that use the same underlying **client relevance** behind the scenes.

### Two options for using these:

- Put the dashboard files in a folder, then load dynamically using the Console's `Load Wizard` option in the Debug Menu.
 - Placing the files in a folder before loading with the console is important, because the console will copy the entire contents of the folder.
- Add the dashboard files to a custom site. 

### Load javascript libraries from CDN with fallback:

    <script src="//ajax.googleapis.com/ajax/libs/jquery/1.5.1/jquery.min.js"></script>
    <script>window.jQuery || document.write('<script src="js/libs/jquery-1.5.1.min.js">\x3C/script>')</script>

### References:

- http://stackoverflow.com/a/9400432/861745
- http://stackoverflow.com/questions/5257923/how-to-load-local-script-files-as-fallback-in-cases-where-cdn-are-blocked-unavai
- http://fallback.io/
 - https://github.com/dolox/fallback/issues/77
- https://github.com/bigfix/adf
- https://bitbucket.org/bigfixme/dashboard-framework

### Examples:

- https://bigfix.me/cdb/dashboard/115