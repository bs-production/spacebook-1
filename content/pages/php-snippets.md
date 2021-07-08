---
title: PHP Snippets
date: 2021-07-08T18:04:53.407Z
permalink: /dev/php.html
eleventyNavigation:
  order: 100
  key: PHP
  parent: Dev
  title: PHP Snippets
---
### Prevent loading CMS Homepage
```php
<?php
// this is here to prevent loading extra homepage content. Remove when we copy stuff into index
global $thePage, $cmsPageData;
if ($thePage == 'index') {
   $cmsPageData['page.body_content'] = '';
}
?>
```

### SVG
```php
<?php echo file_get_contents("http://b388022801b3244fdbae-c913073b3759fb31d6b728a919676eab.r15.cf1.rackcdn.com/v3/templates/icons/basement_waterproofing.svg"); ?>
```

### Direct Traffic 

```php
<?php global $isTrafficDirect;
if($isTrafficDirect) {  ?>

 <?php } ?>
```

### Swap By Month

```php
<?php
    $now   = new DateTime();
    $month = (int)$now->format("m");
    if ($month >= 4 AND $month <= 9) {    
?>
 
Stuff

<?php  }  ?>
```


### Certain dates each year

```php
  <?php
  		if ( time() >= strtotime(date('Y').'-03-10 00:01') && time() < strtotime(date('Y').'-04-06 23:59') )  
  		{         // March / April
	?>
     
<?php
	} // month swap
?>


   <?php if ( time() >= strtotime('2016-05-30 00:01') && time() < strtotime('2016-06-15 23:59') )
            {
            ?>
     <?php
	} // month swap
?>       
            
```

### Display Open Sign by setting Time Zone, Hours & Weekdays

```php
<?php
 date_default_timezone_set('US/Eastern');
 $currenttime = date('h:i:s:u');
 list($hrs,$mins,$secs,$msecs) = split(':',$currenttime);
 /*echo " => $hrs:$mins:$secs\n";*/
?>

<?php
 $now   = new DateTime();
 $hours = (int)$now->format("h");
 $weekdays = (int)$now->format("w");
 if ($hours >= 7 AND $hours <= 17 AND $weekdays >= 1 AND $weekdays <= 5) {
?>

 <div class="opensign"><span>open</span></div>

<?php  }  ?>
```

### Global Variables
```txt
$isCityPage  - Detect City Pages
$isTrafficPpc  - Detech for PPC Traffic Only
$thePage  - Check The Current Page 
$isInHouse - Hide From Building Traffic
$isMobile - Use if you want to load something only on mobile or hide on mobile
```

### URL Parameters
```txt
/?force_source=ppc - Force what a page would look like in ppc
/?force_source=blended - Force what a site would like blended
/?overlay=superawesome  - If you are logged into portal you get some cool stuff
/?opensign=1  - Test Opensign switch to 0 for closed
/sitemap.xml?rebuild=nigh - This will rebuild a site map  
/?devify=1 - Use in CMS pagetree. Fixes some weird dev nav issues.
```


### Custom Tokens 
```php

<?php
	global $siteTokens;
	$siteTokens['http://bonedry.com'] = 'https://www.bonedry.com';  
?>
```
 
### HTTP to HTTPS 
```php
<?php
if (!empty($_SERVER['HTTP_X_FORWARDED_PROTO']) and $_SERVER['HTTP_X_FORWARDED_PROTO'] == 'http') {
    $url = "https://". $_SERVER['SERVER_NAME'] . $_SERVER['REQUEST_URI'];
    header("HTTP/1.1 301 Moved Permanently"); 
    header("Location: $url");
    die();
}
?>
```

### CRM Custom Data 
```php
$siteTokens["[[token_name_here]]"] = "Value"
```
Then in portal you are going to add the label (e.g. crm_label) you want on the left hand column (in crm management) and the token [[token_name_here]] from above in the right hand column. This will get $_POST['crm_label'] = 'Value' sent to the url along with the other data.
 
### Searched Keyword Slider
```php
<?php
        $slideMain = '<div class="main-slide slide1"><div class="row"><div class="columns main-text"><h2>Engineer-Quality Assessments</h2><h3>for All of Your Home\'s Structural Problems</h3><ul><li><a href="/foundation-repair.html">Foundation Repair</a></li><li><a href="/basement-waterproofing.html">Basement Waterproofing</a></li><li><a href="/crawl-space-repair.html">Crawl Space Repair</a></li></ul></div></div></div>';

        $slideFoundation = '<div class="main-slide slide2"><div class="row"><div class="small-12 columns main-slides-text"><h2><a href="/foundation-repair.html">Foundation Issues?</a></h2></div></div></div>';

        $slideConcrete = '<div class="main-slide slide3"><div class="row"><div class="small-12 columns main-slides-text"><h2><a href="/concrete-lifting.html">Concrete Leveling?</a></h2></div></div></div>';

        $slideBasement = '<div class="main-slide slide4"><div class="row"><div class="small-12 columns main-slides-text"><h2><a href="/basement-waterproofing.html">Wet Basement?</a></h2></div></div></div>';

        $slideCrawl = '<div class="main-slide slide5"><div class="row"><div class="small-12 columns main-slides-text"><h2><a href="/crawl-space-repair.html">Wet Crawl Space<br />&amp; sagging floors?</a></h2></div></div></div>';
      ?>

      <?php if(stristr($_SESSION['searchedkeyword'], 'crawl')) {
        echo $slideCrawl . $slideMain . $slideFoundation . $slideConcrete . $slideBasement;
      }
      elseif(stristr($_SESSION['searchedkeyword'], 'basement')) {
        echo $slideBasement . $slideMain . $slideFoundation . $slideConcrete . $slideCrawl;
      }
      elseif(stristr($_SESSION['searchedkeyword'], 'concrete')) {
        echo $slideConcrete . $slideMain . $slideFoundation . $slideBasement . $slideCrawl;
      }
      elseif(stristr($_SESSION['searchedkeyword'], 'foundation')) {
        echo $slideFoundation . $slideMain . $slideBasement . $slideConcrete . $slideCrawl;
      }
      else {
        echo $slideMain . $slideFoundation . $slideConcrete . $slideBasement . $slideCrawl;
      }
      ?>
```


### Geo Date
```php
print_r($_SESSION['client_geo_data']);
```

### Send Data 
```php
$data = array(
        'firstname'  => $_POST[''],
        'lastname' => $_POST[''],
        'phone1' => $_POST[''],
        'email1' => $_POST[''],
        'streetaddress' => $_POST[''],
        'city' => $_POST[''],
        'state' => $_POST[''],
        'zip' => $_POST[''],
        'source' => ' $_POST['']',
        'sourcetype' => ''
    );
    $serialize = http_build_query($data);
    $request = curl_init('url goes here');
    curl_setopt($request, CURLOPT_POST, 1);
    curl_setopt($request, CURLOPT_POSTFIELDS, $serialize);
    curl_setopt($request, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($request, CURLOPT_SSL_VERIFYPEER, false);
    $response = curl_exec($request);
    

    
    curl_close($request);
```

### Add "Sales Rep" field to refer forms
```php
<?php
require_once ENV_ROOT . '/db_wrapper.php';
$db = new db_wrapper('everything');

// company id found in portal>companies>manage companies>choose your company>id in url 
$cidRefer = '1207';
// site id  
$sidRefer = '1381';
// department id for mtt found in cms>widgets>mtt>view all depts>hover dept>id in link 
// to use more than one department, comma separate each id in string below
$didRefer = '2394';

$query = '
	SELECT
	    t.`member.name` AS name
	FROM `everything`.`bsa_team_members` AS t
	           JOIN `everything`.`bsa_team_members_departments` AS d ON d.`department.id` = t.`department.id` AND d.`department.id` IN ('.$didRefer.')
	    LEFT JOIN `everything`.`bsa_team_members_meta` AS tm ON tm.`member.id` = t.`member.id` AND tm.`meta.key` = "youtube_id"
	WHERE
	    t.`company.id` = '.$cidRefer.'
	    AND t.`site.id`  = '.$sidRefer.'
	    AND t.`member.deleted` = 0
	    AND t.`member.live` = 1
	GROUP BY
	    t.`member.name`
	ORDER BY
	    t.`member.name` ASC
';
$salesReps = $db->fetch_all($query);

$salesmen = '';
// build options
foreach ($salesReps as $salesRep) {
    $salesmen .= '<option value="' . $salesRep['name'] . '">' . $salesRep['name'] . '</option>';
}
// build js variable with selector and options and insert it into the form
?>
<script>
    //remove required class if not needed
  salesReps = '<input type="hidden" value="Sales Rep" name="custom_field_1_name" /><div class="comment"><label for="custom_field_1">Your Sales Rep: <span>*</span></label><select name="custom_field_1" style="padding: 0 8px;" class="required" id="SalesRep"><option value="">Please select...</option><?php echo $salesmen; ?></select></div>';
$(document).ready(function(){
    $( "input[name='refer_a_friend']" ).after(salesReps);
});
 
</script>

<script>
    $(document).ready(function() {
        $('form').submit(function() {
            var rep = $("#SalesRep").val(); //capture sale rep
            var mes = $("#Message").val();
            $("#Message").val(mes + '\n' + 'Salesperson: ' + rep); //pass sales rep value to message
            return true;
        });
    });
</script>
```

### Misc
#### If top-level page and silo are not equal
```php
if (!strstr($thePage,'service-area') and !strstr($thePage,'basement-finishing') and !strstr($thePage,'sunroom')) {
}
```


 