---
layout: post
title: "How to use the dev.to API!"
subtitle: "We'll be using PHP to get and display our most recent posts."
date: 2020-07-06
---

## Why?

I use dev.to as my main dev blogging area now, but I want to show-off my blogs on my portfolio! So we're going to create a simple list of the latest 3 blog articles which link back to the dev.to site. For this tutorial I'll be showing how this can be achieved in PHP.

## Let's go!

First of all, the below is a great starting point to understand the dev.to API and all of the possible endpoints.

<a href="https://dev.to/alfredosalzillo/the-state-of-devto-v0-api-1o2">The state of dev.to v0 api</a>

We're going to be using this endpoint: `https://dev.to/api/articles?username=nataliedeweerd` which generates a JSON object with the author's latest 30 articles. To get your personal endpoint, something change the `nataliedeweerd` username to your own.

So how do we get this data into our website? In PHP we can use something called `cURL`. `cURL` (**c**lient **URL**) is a PHP library which allows you to make HTTP requests. So you can call a URL in your code and get a HTML response from it.

The below code shows a basic curl function which gets us our data:

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://dev.to/api/articles?username=nataliedeweerd",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);
```

We need to decode this data before we can effectively use it however. 

```php
$response = json_decode($response, true); 
```

This decodes the json object into a much more usable array! All we need to do now is loop through the array, and print out the results.

```php
foreach ($response as $key => $article){

	echo '
		<a href="'.$article['url'].'" class="blog__article">
			<h2>'.$article['title'].'</h2>
			<div class="blog__description">'.$article['description'].'</div>
			<div class="blog__readmore">Read More</div>
		</a>
	';

	if ($key == 2){ break; }

}
```

Because the array key's are numeric, we can use these to determine how many articles we've printed. If we've printed 3 articles the key will be 2 (array's start from 0 don't forget), so we break out of the foreach.

If you want to have a closer look at what keys the array is printing out, you can use the below code before the foreach loop:

```php
echo '<pre>'.print_r($response,true).'</pre>';
```

This will show you everything the decoded JSON is returning, allowing you to include your article's images, or canonical links, or tags!

And that's it! We just need to apply a bit of CSS and our dev.to articles are printing out wherever we want!