# dark-slack

followed this thread here, but adding my notes to repeate faster:

https://gist.github.com/a7madgamal/c2ce04dde8520f426005e5ed28da8608


I created my css to avoid the one mentioned in the thread getting broke, hacked, changed etc..

https://gist.githubusercontent.com/blabadi/c9191322f25c2b4b0ce36dc0f8f31d2e/raw/ba11420118e94c4094a9f0b4a83789ffdf2cc14a/black_slack.css



1- close (quit for mac) slack

2- go to : 

/Applications/Slack.app/Contents/Resources/app.asar.unpacked/src/static/ssb-interop.js

back it up

3- add to the top of it:

```
document.addEventListener('DOMContentLoaded', function() {
  let tt__customCss = `.menu ul li a:not(.inline_menu_link) {color: #fff !important;}`
  $.ajax({
      url: 'https://gist.githubusercontent.com/blabadi/c9191322f25c2b4b0ce36dc0f8f31d2e/raw/ba11420118e94c4094a9f0b4a83789ffdf2cc14a/black_slack.css',
      success: function(css) {
          $("<style></style>").appendTo('head').html(css + tt__customCss);
          $("<style></style>").appendTo('head').html('#reply_container.upload_in_threads .inline_message_input_container {background: padding-box #545454}');
          $("<style></style>").appendTo('head').html('.p-channel_sidebar {background: #363636 !important}'); 
          $("<style></style>").appendTo('head').html('#client_body:not(.onboarding):not(.feature_global_nav_layout):before {background: inherit;}'); 
      }
  });
});
```

4- start slack 
