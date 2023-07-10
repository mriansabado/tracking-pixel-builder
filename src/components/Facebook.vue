<template>
    <div>
        <div>{{ this.landr }}</div>
    </div>
</template>

<script>
export default {
    data() {
        return {
           landr: '',
        }
    },
    props: {
        pixelID: String,
        LandrEvent: String,
        SerpEvent: String,
        AdclickEvent: String,
        AdclickOnlyEvent: String
    },
    methods: {
        facebookLandr() {
        this.landr = `!function(f,b,e,v,n,t,s)
{if(f.fbq)return;n=f.fbq=function(){n.callMethod?
n.callMethod.apply(n,arguments):n.queue.push(arguments)};
if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
n.queue=[];t=b.createElement(e);t.async=!0;
t.src=v;s=b.getElementsByTagName(e)[0];
s.parentNode.insertBefore(t,s)}(window,document,'script',
'https://connect.facebook.net/en_US/fbevents.js');
 fbq('init', '${this.pixelID}'); 
fbq('track', '${this.LandrEvent}');`
        },
        facebookSerp() {
            return `!function(f,b,e,v,n,t,s)
{if(f.fbq)return;n=f.fbq=function(){n.callMethod?
n.callMethod.apply(n,arguments):n.queue.push(arguments)};
if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
n.queue=[];t=b.createElement(e);t.async=!0;
t.src=v;s=b.getElementsByTagName(e)[0];
s.parentNode.insertBefore(t,s)}(window,document,'script',
'https://connect.facebook.net/en_US/fbevents.js');
 fbq('init', '${this.pixelID}'); 
fbq('track', ‘${this.SerpEvent}’);`
        },
        facebookAdclick() {
            return `focus();
var listener = window.addEventListener("blur", function() {
  active_element = document.activeElement;
  if ("IFRAME" == active_element.tagName && 1 == window.location.href.includes("caf_results")) {
    fbq('track', ‘${this.AdclickEvent}’);
  }
});`
        },
        fbAdclickOnly() {
            return `focus();
var listener = window.addEventListener("blur", function() {
  active_element = document.activeElement;
  if ("IFRAME" == active_element.tagName && 1 == window.location.href.includes("caf_results")) {
    !function(f,b,e,v,n,t,s)
{if(f.fbq)return;n=f.fbq=function(){n.callMethod?
n.callMethod.apply(n,arguments):n.queue.push(arguments)};
if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
n.queue=[];t=b.createElement(e);t.async=!0;
t.src=v;s=b.getElementsByTagName(e)[0];
s.parentNode.insertBefore(t,s)}(window,document,'script',
'https://connect.facebook.net/en_US/fbevents.js');
 fbq('init', '${this.pixelID}'); 
fbq('track', ‘${this.AdclickOnlyEvent}’);
  }
});`
        }
    }
}
</script>