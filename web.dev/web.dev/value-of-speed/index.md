<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format" alt="Aircraft instrument panel, photographer Arie Wubben via unsplash.com" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/lJKAAwKJzlfwFIie0H1o.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#the-value-of-speed" class="w-toc__header--link">The value of speed</a>
--------------------------------------------------------------------------------

-   [Relative Mobile Conversion Rate (Rel mCvR)](#relative-mobile-conversion-rate-(rel-mcvr))
-   [Doing the analysis](#doing-the-analysis)
-   [Things to consider when analyzing Rel mCvR](#things-to-consider-when-analyzing-rel-mcvr)
-   [Summing up](#summing-up)
-   [Next steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

-   <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
-   <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

The value of speed
==================

Show stakeholders how site speed improvements can increase revenue.

Jun 13, 2019 <span class="w-author__separator">•</span> Updated Jun 7, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/8xXS5zjREzCNIpHX3F4h.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Lina Hansson" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8xXS5zjREzCNIpHX3F4h.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8xXS5zjREzCNIpHX3F4h.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8xXS5zjREzCNIpHX3F4h.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8xXS5zjREzCNIpHX3F4h.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8xXS5zjREzCNIpHX3F4h.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/linahansson/)

<a href="/authors/linahansson/" class="w-author__name-link">Lina Hansson</a>

-   <a href="https://twitter.com/LinaCHansson" class="w-author__link">Twitter</a>
-   <a href="https://digies.se" class="w-author__link">Blog</a>

After a lot of hard work, you've done it. You've made your company's site noticeably faster. Now it's time for the fun part: showing stakeholders how much extra revenue your work has generated!

In this post we'll walk through how to do that by calculating the *relative mobile conversion* rate. This metric is useful because it quantifies the effects of site improvements while excluding external factors like marketing campaigns, which can obscure your findings. Let's get started!

Relative Mobile Conversion Rate (Rel mCvR) <a href="#relative-mobile-conversion-rate-(rel-mcvr)" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------

A site's conversion rate can be influenced by site characteristics— like speed and usability—and by external factors—like marketing campaigns, seasonal events, and the mix of marketing channels.

A *conversion* happens when a site visitor becomes a customer. What counts as a conversion will vary depending on the nature of the site. Buying a product, subscribing to a service, registering as a user, or even just viewing a particular page could be considered a conversion. Check with your marketing team if you're not sure how conversions are counted in your company.

Since you're interested in how site speed affects conversions, the mobile site is most relevant— that's where you're most likely to see the benefits of speed improvements. Rather than looking at the mobile conversion rate alone, though, you'll be analyzing the *relative* mobile conversion rate (Rel mCvR), which is calculated by dividing the mobile conversion rate by the desktop conversion rate. This approach reduces the noise from external factors, which tend to affect both desktop and mobile, and makes it easier to see whether any increases in the mobile site's effectiveness were actually caused by the speed improvements.

<img src="https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format" alt="Table showing comparison of mobile/desktop conversion rate and relative mobile conversion rate" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/6q2BiNPameuAqeMOghoE.jpg?auto=format&amp;w=1600 1600w" width="800" height="450" />

**Caution**: Caution: Rel mCvR is influenced not only by speed, but also by other site characteristics like usability. If other big changes were made to the site during the period you want to analyze, you won't be able to measure the effects of speed improvements on their own, but you can show the benefits of all the improvements as a group.

Doing the analysis <a href="#doing-the-analysis" class="w-headline-link">#</a>
------------------------------------------------------------------------------

Make sure you have access to your site's Google Analytics, or collaborate with the analytics team. If you don't have a Google Analytics account, you can learn how to set one up at [Get started with Analytics](https://support.google.com/analytics/answer/1008015?hl=en).

**Step 1:** Go to Google Analytics and click **Admin**. Under **View**, choose **View Settings**. There, copy the View ID.

**Step 2:** Go to [this spreadsheet](https://docs.google.com/spreadsheets/d/13BnREVWPhIiDYdEvOSYP3ovlMggPbnRQPMTSir6y__I/edit#gid=1619071522) and click **File**, and Make a copy.

**Step 3:** Insert the View ID from Google Analytics into field **B3**, **C3** and **D3** in [the spreadsheet](https://docs.google.com/spreadsheets/d/13BnREVWPhIiDYdEvOSYP3ovlMggPbnRQPMTSir6y__I/edit#gid=1619071522). If your Google Analytics has goals instead of Ecommerce Conversion Rate, change field **B6** and **C6** so that you remove `ga:transactionsPerSession` and instead type in `ga:goalConversionRateAll` in the two fields.

**Step 4:** In the spreadsheet, click **Add-ons**, **Google Analytics**, and choose **Run reports**. Then go to the spreadsheet page Rel mCvR and see the results.

You should now have a chart that looks something like this:

<img src="https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format" alt="Chart showing mobile load time vs relative mobile conversion rate." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/d7VY9rh0nPtrfyvctkeb.jpg?auto=format&amp;w=1600 1600w" width="800" height="495" />

**Step 6:** Using the chart, identify a period before the speed optimization (when load times were high) and a period after the speed optimization (when load times should be lower) that you want to analyze. In this example, you would compare eight weeks in Jan–Feb to eight weeks in Aug–Sept.

**Step 7:** In a new sheet, calculate the average load time and rel mCvR for the two periods. Then add the revenue coming from mobile visitors during the period after the speed optimization (Aug–Sept in the example). You can find revenue data in Google Analytics under the section Audience &gt; Mobile &gt; Overview.

<img src="https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format" alt="Screenshot: Image of table in showing revenue data" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/NH6HEdFAmI5IHXOwSPlf.jpg?auto=format&amp;w=1600 1600w" width="800" height="122" />

**Step 8:** Now calculate what the revenue would have been if Rel mCvR had not improved. Do this by dividing the revenue (€1,835,962) by the current Rel mCvR (51%) and multiplying by the Rel mCvR for the period before the speed optimization (42%).

<img src="https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format" alt="Screenshot: spreadsheet cells showing formula for revenue without Rel mCvR improvements" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/HNkshbjj8pYGbGlMoZQ1.jpg?auto=format&amp;w=1600 1600w" width="800" height="202" />

**Step 9:** Subtract the revenue that the company earned from what it would have earned if Rel mCvR had not improved.

<img src="https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format" alt="Screenshot: spreadsheet cells showing extra revenue formula" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/I0LBdqLJ7i9gaTZLqgQc.jpg?auto=format&amp;w=1600 1600w" width="800" height="242" />

In this example, the company earned an additional €323,993 in eight weeks thanks to Rel mCvR improving —that is, thanks to the mobile site becoming faster.

<img src="https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format" alt="Screenshot: spreadsheet cells showing extra revenue due to Rel mCvR improvements" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/ZDZVuXt6QqfXtxkpXcPGfnygYjd2/DhukJqLa37bBxJbkhmaH.jpg?auto=format&amp;w=1600 1600w" width="800" height="242" />

Things to consider when analyzing Rel mCvR <a href="#things-to-consider-when-analyzing-rel-mcvr" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------

As noted above, other changes to the site, such as UX improvements, can influence Rel mCvR.

-   Check that speed was the only big change to the site during the period you want to study. If there were other changes, Rel mCvR can tell you the effect of the changes as a group, but not of an individual change.
-   Watch out for any changes or events that affected the desktop site but not the mobile site —they can skew your results. If you discover any desktop-only changes, omit the affected period from your analysis.
-   You might wonder whether an increase in Rel mCvR is caused by a shift in conversions from desktop to mobile rather than an increase in conversions overall. While there is likely to be some change in the mix of desktop and mobile conversions due to speed improvements, keep in mind that Rel mCvR calculates the mobile conversion rate relative to the desktop conversion rate. So, you only see an increase in Rel mCvR when mCvR goes up more than dCvR. In other words, when doing this calculation you're already counting low, which means you have a safety margin that can compensate for any shifts in the channel mix.

Summing up <a href="#summing-up" class="w-headline-link">#</a>
--------------------------------------------------------------

While it has some limitations, Rel mCvR is a great low-cost way to estimate how much a speed optimization increased revenue without, for example, having to run server-side or slow-down tests. And quantifying the relationship between performance and revenue can help you demonstrate the value of development projects whose benefits might not be immediately clear to non-technical stakeholders.

Next steps <a href="#next-steps" class="w-headline-link">#</a>
--------------------------------------------------------------

-   [Discover performance opportunities with Lighthouse](/discover-performance-opportunities-with-lighthouse)
-   [Performance budgets 101](/performance-budgets-101)

*Aircraft instrument panel image by [Arie Wubben](https://unsplash.com/photos/MHIw0nSxCR4) on [Unsplash](https://unsplash.com/)*

<a href="/tags/analytics/" class="w-chip">Analytics</a> <a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jun 7, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/value-of-speed/index.md)

<a href="/blog" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

-   ### Contribute

    -   <a href="https://github.com/GoogleChrome/web.dev/issues/new?assignees=&amp;labels=bug&amp;template=bug_report.md&amp;title=" class="w-footer__linkbox-link">File a bug</a>
    -   <a href="https://github.com/googlechrome/web.dev" class="w-footer__linkbox-link">View source</a>

-   ### Related content

    -   <a href="https://blog.chromium.org/" class="w-footer__linkbox-link">Chrome updates</a>
    -   <a href="https://developers.google.com/web/" class="w-footer__linkbox-link">Web Fundamentals</a>
    -   <a href="https://developers.google.com/web/showcase/" class="w-footer__linkbox-link">Case studies</a>
    -   <a href="https://devwebfeed.appspot.com/" class="w-footer__linkbox-link">DevWeb Content Firehose</a>
    -   <a href="/podcasts/" class="w-footer__linkbox-link">Podcasts</a>
    -   <a href="/shows/" class="w-footer__linkbox-link">Shows</a>

-   ### Connect

    -   <a href="https://www.twitter.com/ChromiumDev" class="w-footer__linkbox-link">Twitter</a>
    -   <a href="https://www.youtube.com/user/ChromeDevelopers" class="w-footer__linkbox-link">YouTube</a>

<a href="https://developers.google.com/" class="w-footer__utility-logo-link"><img src="/images/lockup-color.png" alt="Google Developers" class="w-footer__utility-logo" width="185" height="33" /></a>

-   <a href="https://developer.chrome.com/" class="w-footer__utility-link">Chrome</a>
-   <a href="https://firebase.google.com/" class="w-footer__utility-link">Firebase</a>
-   <a href="https://cloud.google.com/" class="w-footer__utility-link">Google Cloud Platform</a>
-   <a href="https://developers.google.com/products" class="w-footer__utility-link">All products</a>

<!-- -->

-   <a href="https://policies.google.com/" class="w-footer__utility-link">Terms &amp; Privacy</a>
-   <a href="/community-guidelines/" class="w-footer__utility-link">Community Guidelines</a>

Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/terms/site-policies).
