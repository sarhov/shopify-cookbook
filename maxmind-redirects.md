---
layout: post
title: Maxmind redirects
excerpt: "Using the below js format (simplified from maxminds sample here: http://dev.maxmind.com/geoip/geoip2/javascript/tutorial/) to look for the region codes and then redirect to a specific url separately"
---
{% raw %}

# Redirect Users to a Country-Specific Site using Maxmind

Using the below js format (simplified from maxminds sample here: http://dev.maxmind.com/geoip/geoip2/javascript/tutorial/) to look for the region codes and then redirect to a specific url separately - reasons:
* GB was the region code for the UK  - but wasn't part of the url
* despite maxminds claim to capture EU as a continent this wasn't redirecting - therefore all country codes need to be listed for Europe.


```
<script src="//js.maxmind.com/js/apis/geoip2/v2.1/geoip2.js" type="text/javascript"></script>


<script language="JavaScript">

document.addEventListener("DOMContentLoaded", function(event) { 

	geoip2.country(
	    function (response) {
	        if (response.country.iso_code == "AU") {
	            window.location = "https://au.kirstinash.com"
	        }

	        else if (response.country.iso_code == "EU" || "AD" || "AL" || "AT" || "BA" || "BE" || "BG" || "BY" || "CH" || "CS" || "CZ" || "DE" || "DK" || "EE" || "ES" || "FI" || "FO" || "FR" || "FX" || "GI" || "GR" || "HR" || "HU" || "IE" || "IS" || "IT" || "LI" || "LT" || "LU" || "LV" || "MC" || "MD" || "MK" || "MT" || "NL" || "NO" || "PL" || "PT" || "RO" || "SE" || "SI" || "SJ" || "SK" || "SM" || "UA" || "VA") {
	            window.location = "https://eu.kirstinash.com"
	        }

	        else if (response.country.iso_code == "NZ") {
	            window.location = "https://nz.kirstinash.com"
	        }

	        else if (response.country.iso_code == "GB") {
	            window.location = "https://uk.kirstinash.com"
	        }

	        else if (response.country.iso_code == "US") {
	            window.location = "https://us.kirstinash.com"
	        }

	        else {
	            window.location = "https://au.kirstinash.com"
	        }
	    }
	);
});
</script>
```

### VPN testing:
The maxmind API uses IP rather than geolocation coordinates - so a VPN is needed for tests rather than the chrome dev Sensor tool.

##### js guides:
http://dev.maxmind.com/geoip/geoip2/javascript/tutorial/

##### EU country codes:
http://dev.maxmind.com/geoip/legacy/codes/eu_country_list/



{% endraw %}

