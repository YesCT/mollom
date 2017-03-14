Mollom
======

Integrates with the Mollom service: https://www.mollom.com

Installation
------------

- Install this module using the official Backdrop CMS instructions at
  https://backdropcms.org/guide/modules

- Go to https://www.mollom.com,

  - sign up or log in with your account
  - go to your Site manager ("Manage sites" link in the upper right)
  - create a site (API keys) for this Drupal installation.

- Enter your API keys on Administration > Configuration > Content authoring
  > Mollom > Settings (admin/config/content/mollom).

- If your site runs behind a reverse proxy or load balancer:

  - Open sites/default/settings.php in a text editor.
  - Ensure that the "reverse_proxy" settings are enabled and configured
    correctly.

  Your site MUST send the actual/proper IP address for every site visitor to
  Mollom.  You can confirm that your configuration is correct by going to
  Reports > "Recent log messages".  In the details of each log entry, you should
  see a different IP address for each site visitor in the "Hostname" field.
  If you see the same IP address for different visitors, then your reverse proxy
  configuration is not correct.

- On servers running PHP <5.4, and PHP as CGI (not Apache module), inbound HTTP
  request headers are not made available to PHP.  Add the following lines to
  your .htaccess file:

    RewriteEngine On
    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

- (optional) Download and enable the libraries module:
  http://drupal.org/project/libraries

- (optional) Download the chosen JavaScript plugin into your libraries location
  - Download from https://github.com/harvesthq/chosen/releases
    and save in your libraries location in a new "chosen" folder.
  - See instructions from the libraries module for details:
    https://www.drupal.org/node/1440066
    
- Enable and configure each form that you want to protect with Mollom:
  
  * Go to Administration > Configuration > Content authoring > Mollom.
  
  * Add a form to protect and configure the options as desired.
  
  Note the "bypass permissions" for each protected form:  If the currently
  logged-in user has any of the listed permissions, then Mollom is NOT involved
  in the form submission (at all).
  
Testing
-------
  
Do NOT test Mollom without enabling the testing mode.  Doing so would negatively
affect your own author reputation across all sites in the Mollom network.
  
To test Mollom:
  
- Go to Administration > Configuration > Content authoring > Mollom > Settings.
  
- Enable the "Testing mode" option.
  Note: Ensure to read the difference in behavior.

- Log out or switch to a different user, and perform your tests.

- Disable the testing mode once you're done with testing.

Documentation
-------------

Additional documentation is located in the Wiki:
https://github.com/backdrop-contrib/mollom/wiki/Documentation

For questions pertaining to the Mollom service go to
https://www.mollom.com/support

Issues
------

Bugs and Feature requests should be reported in the Issue Queue:
https://github.com/backdrop-contrib/mollom/issues

For issues pertaining to the Mollom service, for example, inappropriately
blocked posts, spam posts getting through, etc., contact Mollom Support:
https://www.mollom.com/contact
  - Ensure to include the Mollom session/content IDs of affected posts; find
    them in Drupal's Recent log messages by filtering by the "mollom" category.

Current Maintainers
-------------------

- Cathy Theys (https://github.com/YesCT)
- Seeking additional maintainers

Credits
-------

- Ported to Backdrop CMS by Cathy Theys (https://github.com/YesCT).
- Maintained for Drupal by Lisa Backer (https://www.drupal.org/u/eshta).
- Maintained for Drupal by Nick Veenhof (https://www.drupal.org/u/nick_vh).
- Maintained for Drupal by Daniel F. Kudwien (https://www.drupal.org/u/sun).
- Originally written for Drupal by Dries Buytaert (https://www.drupal.org/u/dries).

License
-------

This project is GPL v2 software. See the LICENSE.txt file in this directory for
complete text.
