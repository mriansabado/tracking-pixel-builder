<template>
<div id="main" class="container">
   <div class="columns">
       <div class="column is-full max-col-width">
    <!-- Traffic and Pixel ID -->
            <div class="box">
                <label class="label">Pixel Craft - Crafting Pixels for your Ads</label>
            </div>
            <div class="box">
                <div>
                    <label class="label">Traffic</label>
                    <div class="control">
                        <div class="select">
                            <select v-model="traffic">
                                <option value="Facebook">Facebook</option>
                                <option value="Tiktok">Tiktok</option>
                                <option value="Taboola">Taboola</option>
                                <option value="Outbrain">Outbrain</option>
                                <!-- <option value="GoogleGTM">Google GTM (Under Development)</option> -->
                            </select>
                        </div>
                    </div>
                    <span class="ml-2 has-text-danger" v-if="warningTraffic">! Select a Traffic Source</span>
                </div>
                <div class="column mt-5">
                    <label class=" pt-4 has-text-weight-bold">Pixel ID</label>
                    <input class="input" v-model="pixelID" type="text">
                    <span class="ml-2 has-text-danger" v-if="warningPixelID">! Enter a Pixel ID</span>
                </div>
            
<!-- Pixel Events -->
                <hr>
                <div class="mt-5">
                    <input v-model="placementLandr" type="checkbox">
                    <label class="is-inline ml-3 label">Lander</label>
                    <div class="column">
                        <div v-if="traffic == 'Facebook' || traffic == 'Tiktok'">
                            <div class="control">
                                <div class="select">
                                    <select v-model="LandrEvent">
                                        <option v-if="traffic == 'Facebook'" value="'AddPaymentInfo'">Add Payment Info</option>
                                        <option v-if="traffic == 'Facebook'" value="AddToCart">Add To Cart</option>
                                        <option v-if="traffic == 'Facebook'" value="CompleteRegistration">Complete Registration</option>
                                        <option v-if="traffic == 'Facebook'" value="InitiateCheckout">Initiate Checkout</option>
                                        <option v-if="traffic == 'Facebook'" value="Lead">Lead</option>
                                        <option v-if="traffic == 'Facebook'" value="PageView">Page View</option>
                                        <option v-if="traffic == 'Facebook'" value="Purchase">Purchase</option>
                                        <option v-if="traffic == 'Facebook'" value="Search">Search</option>
                                        <option v-if="traffic == 'Facebook'" value="ViewContent">View Content</option>
                                        <option v-if="traffic == 'Tiktok'" value="AddToCart">Add To Cart</option>
                                        <option v-if="traffic == 'Tiktok'" value="AddPaymentInfo">Add Payment Info</option>
                                        <option v-if="traffic == 'Tiktok'" value="AddToWishlist">Add To Wishlist</option>
                                        <option v-if="traffic == 'Tiktok'" value="ClickButton">Click Button</option>
                                        <option v-if="traffic == 'Tiktok'" value="CompletePayment">Complete Payment</option>
                                        <option v-if="traffic == 'Tiktok'" value="CompleteRegistration">Complete Registration</option> 
                                        <option v-if="traffic == 'Tiktok'" value="InitiateCheckout">Initiate Checkout</option>
                                        <option v-if="traffic == 'Tiktok'" value="ViewContent">View Content</option>
                                        <option v-if="traffic == 'Tiktok'" value="Search">Search</option>
                                    </select>
                                </div>
                            </div>
                        </div>
                        <div v-if="traffic == 'Taboola'">
                            <input class="input" type="text" placeholder="input Taboola event..." v-model="taboolaLandrEvent">
                        </div>
                        <div v-if="traffic == 'Outbrain'">
                            <input class="input" type="text" placeholder="input Outbran event..." v-model="outbrainLandrEvent">
                        </div>
                        <div v-if="traffic == 'GoogleGTM'">
                            <input class="input" type="text" placeholder="input GTM Pixel ID" v-model="gtmLanderEvent">
                        </div>
                    </div>
                </div>
                <hr>
                <div class="mt-5">
                    <input v-model="placementSerp" type="checkbox">
                    <label class="is-inline ml-3 label">Serp</label>
                     <div class="column">
                        <div v-if="traffic == 'Facebook' || traffic == 'Tiktok'">
                            <div class="control">
                                <div class="select">
                                    <select v-model="SerpEvent">
                                        <option v-if="traffic == 'Facebook'" value="'AddPaymentInfo'">Add Payment Info</option>
                                        <option v-if="traffic == 'Facebook'" value="AddToCart">Add To Cart</option>
                                        <option v-if="traffic == 'Facebook'" value="CompleteRegistration">Complete Registration</option>
                                        <option v-if="traffic == 'Facebook'" value="InitiateCheckout">Initiate Checkout</option>
                                        <option v-if="traffic == 'Facebook'" value="Lead">Lead</option>
                                        <option v-if="traffic == 'Facebook'" value="PageView">Page View</option>
                                        <option v-if="traffic == 'Facebook'" value="Purchase">Purchase</option>
                                        <option v-if="traffic == 'Facebook'" value="Search">Search</option>
                                        <option v-if="traffic == 'Facebook'" value="ViewContent">View Content</option>
                                        <option v-if="traffic == 'Tiktok'" value="AddToCart">Add To Cart</option>
                                        <option v-if="traffic == 'Tiktok'" value="AddPaymentInfo">Add Payment Info</option>
                                        <option v-if="traffic == 'Tiktok'" value="AddToWishlist">Add To Wishlist</option>
                                        <option v-if="traffic == 'Tiktok'" value="ClickButton">Click Button</option>
                                        <option v-if="traffic == 'Tiktok'" value="CompletePayment">Complete Payment</option>
                                        <option v-if="traffic == 'Tiktok'" value="CompleteRegistration">Complete Registration</option> 
                                        <option v-if="traffic == 'Tiktok'" value="InitiateCheckout">Initiate Checkout</option>
                                        <option v-if="traffic == 'Tiktok'" value="ViewContent">View Content</option>
                                        <option v-if="traffic == 'Tiktok'" value="Search">Search</option>
                                    </select>
                                </div>
                            </div>
                        </div>
                        <div v-if="traffic == 'Taboola'">
                            <input class="input" type="text" placeholder="input Taboola event..." v-model="taboolaSerpEvent">
                        </div>
                        <div v-if="traffic == 'Outbrain'">
                            <input class="input" type="text" placeholder="input Outbrain event..." v-model="outbrainSerpEvent">
                        </div>
                        <div v-if="traffic == 'GoogleGTM'">
                            <input class="input" type="text" placeholder="input GTM Pixel ID" v-model="gtmSerpEvent">
                        </div>
                    </div>
                </div>
                <hr>
                <div class="mt-5">
                    <input v-model="placementAdclick" type="checkbox">
                    <label class="is-inline ml-3 label">Ad Click</label>
                    <div class="column">
                        <div v-if="traffic == 'Facebook' || traffic == 'Tiktok'">
                            <div class="control">
                                <div class="select">
                                    <select v-model="AdclickEvent">
                                        <option v-if="traffic == 'Facebook'" value="'AddPaymentInfo'">Add Payment Info</option>
                                        <option v-if="traffic == 'Facebook'" value="AddToCart">Add To Cart</option>
                                        <option v-if="traffic == 'Facebook'" value="CompleteRegistration">Complete Registration</option>
                                        <option v-if="traffic == 'Facebook'" value="InitiateCheckout">Initiate Checkout</option>
                                        <option v-if="traffic == 'Facebook'" value="Lead">Lead</option>
                                        <option v-if="traffic == 'Facebook'" value="PageView">Page View</option>
                                        <option v-if="traffic == 'Facebook'" value="Purchase">Purchase</option>
                                        <option v-if="traffic == 'Facebook'" value="Search">Search</option>
                                        <option v-if="traffic == 'Facebook'" value="ViewContent">View Content</option>
                                        <option v-if="traffic == 'Tiktok'" value="AddToCart">Add To Cart</option>
                                        <option v-if="traffic == 'Tiktok'" value="AddPaymentInfo">Add Payment Info</option>
                                        <option v-if="traffic == 'Tiktok'" value="AddToWishlist">Add To Wishlist</option>
                                        <option v-if="traffic == 'Tiktok'" value="ClickButton">Click Button</option>
                                        <option v-if="traffic == 'Tiktok'" value="CompletePayment">Complete Payment</option>
                                        <option v-if="traffic == 'Tiktok'" value="CompleteRegistration">Complete Registration</option> 
                                        <option v-if="traffic == 'Tiktok'" value="InitiateCheckout">Initiate Checkout</option>
                                        <option v-if="traffic == 'Tiktok'" value="ViewContent">View Content</option>
                                        <option v-if="traffic == 'Tiktok'" value="Search">Search</option>
                                    </select>
                                </div>
                            </div>
                        </div>
                    <div v-if="traffic == 'Taboola'">
                        <input class="input" type="text" placeholder="input Taboola event..." v-model="taboolaAdclickEvent">
                    </div>
                    <div v-if="traffic == 'Outbrain'">
                        <input class="input" type="text" placeholder="input Outbrain event..." v-model="outbrainAdClickEvent">
                    </div>
                     <div v-if="traffic == 'GoogleGTM'">
                        <input class="input" type="text" placeholder="input GTM Pixel ID" v-model="gtmAdClickEvent">
                    </div>
                    </div>
                </div>


                  <!-- Check for Estimated CPC -->
                <div v-if="traffic == 'Facebook'" class="is-flex is-justify-content-space-between">
                    <div>
                        <label class="is-inline ml-3 label">Add Estimated CPC?</label>
                        <input type="checkbox" class="ml-3" v-model="enableEstimatedCPC">
                    </div>
                </div>
                 <!-- Add Estimated CPC --> 
                <div v-if="enableEstimatedCPC" class="is-flex is-align-items-center" style="gap: 1rem;">
                    <input type="number" 
                           class="input" 
                           v-model="cpcNumber" 
                           placeholder="Enter CPC number" 
                           style="width: 150px; min-width: 120px; max-width: 200px;">
                    
                    <div class="select" style="min-width: 300px; max-width: 500px;">
                        <select v-model="estimatedCPCValue">
                            <option value="">Select CPC</option>
                            <option :value="`{$estimatedGoogleCPC_${cpcNumber}}`">estimatedGoogleCPC -- Last 3 Days Rolling Average</option>
                            <option :value="`{$estimatedGoogleCPCToday_${cpcNumber}}`">estimatedGoogleCPCToday -- Today's Average</option>
                            <option :value="`{$estimatedGoogleCPCYesterday_${cpcNumber}}`">estimatedGoogleCPCYesterday -- Yesterday's Average</option>
                            <option :value="`{$estimatedGoogleCPCNow_${cpcNumber}}`">estimatedGoogleCPCNow - Last Hour Average</option>
                        </select>
                    </div>
                </div>
                <hr>
                <!-- End of Estimated CPC -->
                <div>
                    <div class="container has-text-right">
                        <button class="button is-success" @click="this.fireAll">Make Pixel</button>
                        <button class="button is-danger ml-5" @click="this.reset">Reset</button>
                    </div>
                </div>
            </div>
           
       </div>
<!-- Results Area -->
        <div class="column is-full max-col-width is-flex-direction-column">
            <div class="field">
                <div class="control">
                    <div class="textarea is-large landrTextArea">
                    <div>
                        <label class="label is-inline">Lander</label>
                        <button @click="this.copyTextLandr" class="is-inline button is-small is-warning is-rounded ml-3 mt-1">copy</button>
                        <p v-if="this.copiedLandr" class="is-inline has-text-danger is-size-7 ml-3 copied-text">Text Copied to Clipboard</p>
                    </div>
                        <hr>
                        <div ref="landrRef" v-if="traffic == 'Facebook' && placementLandr" class="pixel-text"> 
                            {{ fbLandrResult }}
                        </div>
                        <div ref="landrRef" v-if="traffic == 'Tiktok' && placementLandr" class="pixel-text">
                            {{ ttLandrResult }}
                        </div>
                        <div ref="landrRef" v-if="traffic == 'Taboola' && placementLandr" class="pixel-text">
                            {{ taboolaLandrResult }}
                        </div>
                        <div ref="landrRef" v-if="traffic == 'Outbrain' && placementLandr" class="pixel-text">
                            {{ outbrainLandrResult }}
                        </div>
                        <span v-else></span>
                    </div>
                </div>
                <div class="control mt-4">
                     <div class="textarea is-large serpTextArea">
                    <div>
                        <label class="label is-inline">Serp</label>
                        <button @click="this.copyTextSerp" class="is-inline button is-small is-warning is-rounded ml-3 mt-1">copy</button>
                        <p v-if="this.copiedSerp" class="is-inline has-text-danger is-size-7 ml-3 copied-text">Text Copied to Clipboard</p>
                    </div>
                     <hr>
                     <div ref="serpRef">
                        <div v-if="traffic == 'Facebook' && placementSerp" class="pixel-text">
                            {{ fbSerpResult }}
                        </div>
                        <div v-if="traffic == 'Tiktok' && placementSerp" class="pixel-text">
                            {{ ttSerpResult }}
                        </div>
                        <div v-if="traffic == 'Taboola' && placementSerp" class="pixel-text">
                            {{ taboolaSerpResult }}
                        </div>
                        <div v-if="traffic == 'Outbrain' && placementSerp" class="pixel-text">
                            {{ outbrainSerpResult }}
                        </div>
                        
                         <div v-if="traffic == 'Facebook' && placementAdclick && placementSerp" class="pixel-text">
                            {{ fbAdclickResult }}
                        </div>
                        <div v-if="traffic == 'Facebook' && placementAdclick && !placementSerp" class="pixel-text">
                            {{ fbAdclickOnlyResult }}
                        </div>
                        <div v-if="traffic == 'Tiktok' && placementAdclick && placementSerp" class="pixel-text">
                            {{ ttAdclickResult }}
                        </div>
                       <div v-if="traffic == 'Tiktok' && placementAdclick && !placementSerp" class="pixel-text">
                            {{ ttAdclickOnlyResult }}
                        </div>
                        <div v-if="traffic == 'Taboola' && placementAdclick && placementSerp" class="pixel-text">
                            {{ taboolaAdclickResult }}
                        </div>
                        <div v-if="traffic == 'Taboola' && placementAdclick && !placementSerp" class="pixel-text">
                            {{ taboolaAdclickOnlyResult }}
                        </div>
                        <div v-if="traffic == 'Outbrain' && placementAdclick && placementSerp" class="pixel-text">
                            {{ outbrainAdclickResult }}
                        </div>
                        <div v-if="traffic == 'Outbrain' && placementAdclick && !placementSerp" class="pixel-text">
                            {{ outbrainAdclickOnlyResult }}
                        </div>
                    </div>
                </div>
                </div>
            </div>

<!-- AdClick Only -->
            
           
        </div>
   </div>
</div>
<hr>
    
</template>

<script>
export default {
    data() {
        return {
            traffic: "",
            warningTraffic: false,
            warningPixelID: false,
            fbLandrResult: "",
            fbSerpResult: "",
            fbAdclickResult: "",
            fbAdclickOnlyResult: "",
            fbLandrAdclickOnlyResult: "",
            ttLandrResult: "",
            ttSerpResult: "",
            ttAdclickResult: "",
            ttAdclickOnlyResult: "",
            pixelID: "",
            LandrEvent: "",
            SerpEvent: "",
            AdclickEvent: "",
            AdclickOnlyEvent: "",
            ttLandrEvent: "",
            ttSerpEvent: "",
            ttAdclickEvent: "",
            ttAdclickOnlyEvent: "",
            taboolaLandrEvent: "",
            taboolaSerpEvent: "",
            taboolaAdClickEvent: "",
            taboolaAdclickOnlyEvent: "",
            taboolaLandrResult: "",
            taboolaSerpResult: "",
            taboolaAdclickResult: "",
            taboolaAdclickOnlyResult: "",
            outbrainLandrEvent: "",
            outbrainSerpEvent: "",
            outbrainAdClickEvent: "",
            outbrainAdClickOnlyEvent: "",
            outbrainLandrResult: "",
            outbrainSerpResult: "",
            outbrainAdclickResult: "",
            outbrainAdclickOnlyResult: "",
            gtmLanderEvent: "",
            gtmSerpEvent: "",
            gtmAdClickEvent: "",
            gtmAdClickOnlyEvent: "",
            gtmLandrResult: "",
            gtmSerpResult: "",
            gtmAdClickResult: "",
            gtmAdClickOnlyResult: "",
            adClick: false,
            placementLandr: false,
            placementSerp: false,
            placementAdclick: false,
            placementAdclickOnly: false,
            postback: false,
            postbackResult: "",
            copiedLandr: false,
            copiedSerp: false,
            postbackURL: "",
            copiedPostback: false,
            adClickPostback: false,
            adClickPostbackResult: "",
            adClickText: false,
            estimatedCPC: false,
            cpcNumber: 0,
            estimatedCPCValue: "",
            enableEstimatedCPC: false,
        };
    },
    watch: {
        cpcNumber(newVal) {
            console.log(`cpcNumber changed to: ${newVal}`);
        }
    },
    methods: {
        copyTextLandr() {
            const text = this.$refs.landrRef.innerText;
            navigator.clipboard.writeText(text)
                .then(() => {
                this.copiedLandr = true;
            })
                .catch((error) => {
                alert("Failed to copy text " + error);
            });
        },
        copyTextSerp() {
            const text = this.$refs.serpRef.innerText;
            navigator.clipboard.writeText(text)
                .then(() => {
                this.copiedSerp = true;
            })
                .catch((error) => {
                alert("Failed to copy text " + error);
            });
        },
        reset() {
            location.reload();
        },
        fireAll() {
            if (!this.traffic) {
                this.warningTraffic = true;
                return;
            }
            else if (!this.pixelID) {
                this.warningTraffic = false;
                this.warningPixelID = true;
                return;
            }
            else {
                this.warningTraffic = false;
                this.warningPixelID = false;
                this.fbLandr();
                this.fbSerp();
                this.fbAdclick();
                this.fbAdclickOnly();
                this.ttLandr();
                this.ttSerp();
                this.ttAdclick();
                this.ttAdclickOnly();
                this.taboolaLandr();
                this.taboolaSerp();
                this.taboolaAdClick();
                this.taboolaAdClickOnly();
                this.outbrainLandr();
                this.outbrainSerp();
                this.outbrainAdclick();
                this.outbrainAdclickOnly();
            }
        },
        fireAdClickOnly() {
            if (!this.traffic) {
                this.warningTraffic = true;
                return;
            }
            else if (!this.pixelID) {
                this.warningTraffic = false;
                this.warningPixelID = true;
                return;
            }
            else {
                this.warningTraffic = false;
                this.warningPixelID = false;
                
            }
        },

    // Facebook
fbLandr() {
    this.fbLandrResult = `
!function(f,b,e,v,n,t,s)
{if(f.fbq)return;n=f.fbq=function(){n.callMethod?
n.callMethod.apply(n,arguments):n.queue.push(arguments)};
if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
n.queue=[];t=b.createElement(e);t.async=!0;
t.src=v;s=b.getElementsByTagName(e)[0];
s.parentNode.insertBefore(t,s)}(window,document,'script',
'https://connect.facebook.net/en_US/fbevents.js');
fbq('init', '${this.pixelID}'); 
fbq('track', '${this.LandrEvent}',{}, {eventID: '{$uuid}'});
`;
    },

fbSerp() {
    this.fbSerpResult = `
!function(f,b,e,v,n,t,s)
{if(f.fbq)return;n=f.fbq=function(){n.callMethod?
n.callMethod.apply(n,arguments):n.queue.push(arguments)};
if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
n.queue=[];t=b.createElement(e);t.async=!0;
t.src=v;s=b.getElementsByTagName(e)[0];
s.parentNode.insertBefore(t,s)}(window,document,'script',
'https://connect.facebook.net/en_US/fbevents.js');
fbq('init', '${this.pixelID}'); 
fbq('track', '${this.SerpEvent}',{}, {eventID: '{$uuid}'});
`;
    },

fbAdclick() {
    this.adClick = true;
    this.fbAdclickResult = `
focus();
var listener = window.addEventListener("blur", function() {
active_element = document.activeElement;
if ("IFRAME" == active_element.tagName && 1 == window.location.href.includes("caf_results")) {
fbq('track', '${this.AdclickEvent}',
{value: '${this.estimatedCPCValue}'}, 
{eventID: '{$uuid}'});
}
});`;
    },

fbAdclickOnly() {
    this.fbAdclickOnlyResult = 
`
focus();
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
fbq('track', '${this.AdclickEvent}',
{value: '${this.estimatedCPCValue}'},
{eventID: '{$uuid}'});
}
});`;
    },
// Tiktok
ttLandr() {
    this.ttLandrResult = `
!function (w, d, t) {
w.TiktokAnalyticsObject=t;var ttq=w[t]=w[t]||[];ttq.methods=["page","track","identify","instances","debug","on","off","once","ready","alias","group","enableCookie","disableCookie"],
ttq.setAndDefer=function(t,e){t[e]=function(){t.push([e].concat(Array.prototype.slice.call(arguments,0)))}};
for(var i=0;i<ttq.methods.length;i++)ttq.setAndDefer(ttq,ttq.methods[i]);
ttq.instance=function(t){for(var e=ttq._i[t]||[],n=0;n<ttq.methods.length;n++)ttq.setAndDefer(e,ttq.methods[n]);
return e},ttq.load=function(e,n){var i="https://analytics.tiktok.com/i18n/pixel/events.js";
ttq._i=ttq._i||{},ttq._i[e]=[],ttq._i[e]._u=i,ttq._t=ttq._t||{},ttq._t[e]=+new Date,ttq._o=ttq._o||{},ttq._o[e]=n||{};
var o=document.createElement("script");o.type="text/javascript",o.async=!0,o.src=i+"?sdkid="+e+"&lib="+t;var a=document.getElementsByTagName("script")[0];a.parentNode.insertBefore(o,a)};

ttq.load('${this.pixelID}');
ttq.track('${this.LandrEvent}');
ttq.page();
}(window, document, 'ttq');`;
    },

ttSerp() {
    this.ttSerpResult = `
!function (w, d, t) {
w.TiktokAnalyticsObject=t;var ttq=w[t]=w[t]||[];ttq.methods=["page","track","identify","instances","debug","on","off","once","ready","alias","group","enableCookie","disableCookie"],
ttq.setAndDefer=function(t,e){t[e]=function(){t.push([e].concat(Array.prototype.slice.call(arguments,0)))}};
for(var i=0;i<ttq.methods.length;i++)ttq.setAndDefer(ttq,ttq.methods[i]);ttq.instance=function(t){for(var e=ttq._i[t]||[],n=0;n<ttq.methods.length;n++)ttq.setAndDefer(e,ttq.methods[n]);
return e},ttq.load=function(e,n){var i="https://analytics.tiktok.com/i18n/pixel/events.js";
ttq._i=ttq._i||{},ttq._i[e]=[],ttq._i[e]._u=i,ttq._t=ttq._t||{},ttq._t[e]=+new Date,ttq._o=ttq._o||{},ttq._o[e]=n||{};
var o=document.createElement("script");o.type="text/javascript",o.async=!0,o.src=i+"?sdkid="+e+"&lib="+t;var a=document.getElementsByTagName("script")[0];a.parentNode.insertBefore(o,a)};
ttq.load('${this.pixelID}');
ttq.track('${this.SerpEvent}');
ttq.page();
}(window, document, 'ttq');`;
    },

ttAdclick() {
    this.ttAdclickResult = `
focus();
var listener = window.addEventListener("blur", function() {
active_element = document.activeElement;
if ("IFRAME" == active_element.tagName && 1 == window.location.href.includes("caf_results")) {
    ttq.track('${this.AdclickEvent}');
    }
});`;
        },

ttAdclickOnly() {
    this.ttAdclickOnlyResult = `
focus();
var listener = window.addEventListener("blur", function() {
active_element = document.activeElement;
if ("IFRAME" == active_element.tagName && 1 == window.location.href.includes("caf_results")) {
!function (w, d, t) {
w.TiktokAnalyticsObject=t;var ttq=w[t]=w[t]||[];ttq.methods=["page","track","identify","instances","debug","on","off","once","ready","alias","group","enableCookie","disableCookie"],ttq.setAndDefer=function(t,e){t[e]=function(){t.push([e].concat(Array.prototype.slice.call(arguments,0)))}};for(var 
i=0;i<ttq.methods.length;i++)ttq.setAndDefer(ttq,ttq.methods[i]);ttq.instance=function(t){for(var e=ttq._i[t]||[],n=0;n<ttq.methods.length;n++)ttq.setAndDefer(e,ttq.methods[n]);return e},ttq.load=function(e,n){var i="https://analytics.tiktok.com/i18n/pixel/events.js";ttq._i=ttq._i||{},ttq._i[e]=[],ttq._i[e]._u=i,ttq._t=ttq._t||{},ttq._t[e]=+new Date,ttq._o=ttq._o||{},ttq._o[e]=n||{};var o=document.createElement("script");o.type="text/javascript",o.async=!0,o.src=i+"?sdkid="+e+"&lib="+t;var a=document.getElementsByTagName("script")[0];a.parentNode.insertBefore(o,a)};

ttq.load('${this.pixelID}');
ttq.track('${this.AdclickEvent}');
ttq.page();
}(window, document, 'ttq');

}
});`;
        },
 // Taboola
taboolaLandr() {
    this.taboolaLandrResult = `
window._tfa = window._tfa || [];
window._tfa.push({notify: 'event', name: 'page_view', id: ${this.pixelID}});
!function (t, f, a, x) {
if (!document.getElementById(x)) {
t.async = 1;t.src = a;t.id=x;f.parentNode.insertBefore(t, f);
}}(document.createElement('script'),
document.getElementsByTagName('script')[0],
'//cdn.taboola.com/libtrc/unip/${this.pixelID}/tfa.js',
'tb_tfa_script');
_tfa.push({notify: 'event', name: '${this.taboolaLandrEvent}', id: ${this.pixelID}});
`;
    },
taboolaSerp() {
    this.taboolaSerpResult = `
window._tfa = window._tfa || [];
window._tfa.push({notify: 'event', name: 'page_view', id: ${this.pixelID}});
!function (t, f, a, x) {
if (!document.getElementById(x)) {
t.async = 1;t.src = a;t.id=x;f.parentNode.insertBefore(t, f);
}}(document.createElement('script'),
document.getElementsByTagName('script')[0],
'//cdn.taboola.com/libtrc/unip/${this.pixelID}/tfa.js',
'tb_tfa_script');
_tfa.push({notify: 'event', name: '${this.taboolaSerpEvent}', id: ${this.pixelID}});
`;
    },
taboolaAdClick() {
    this.taboolaAdclickResult = `
focus();var listener = window.addEventListener("blur", function() {
active_element = document.activeElement;
if ("IFRAME" == active_element.tagName && 1 == window.location.href.includes("caf_results")) {
_tfa.push({notify: 'event', name: '${this.taboolaAdclickEvent}', id: ${this.pixelID}});
}
});`;
    },
taboolaAdClickOnly() {
    this.taboolaAdclickOnlyResult = `
focus();
var listener = window.addEventListener("blur", function() {
active_element = document.activeElement;
if ("IFRAME" == active_element.tagName && 1 == window.location.href.includes("caf_results")) {
window._tfa = window._tfa || [];
window._tfa.push({notify: 'event', name: 'page_view', id: ${this.pixelID}});
!function (t, f, a, x) {
if (!document.getElementById(x)) {
t.async = 1;t.src = a;t.id=x;f.parentNode.insertBefore(t, f);
}}(document.createElement('script'),
document.getElementsByTagName('script')[0],
'//cdn.taboola.com/libtrc/unip/${this.pixelID}/tfa.js',
'tb_tfa_script');
_tfa.push({notify: 'event', name: '${this.taboolaAdclickEvent}', id: ${this.pixelID}});
}
});`;
    },
// Outbrain
outbrainLandr() {
        this.outbrainLandrResult = `
!function(_window, _document) {
var OB_ADV_ID='${this.pixelID}';
if (_window.obApi) {var toArray = function(object) {return Object.prototype.toString.call(object) === '[object Array]' ? object : [object];};_window.obApi.marketerId = toArray(_window.obApi.marketerId).concat(toArray(OB_ADV_ID));return;}
var api = _window.obApi = function() {api.dispatch ? api.dispatch.apply(api, arguments) : api.queue.push(arguments);};api.version = '1.1';api.loaded = true;api.marketerId = OB_ADV_ID;api.queue = [];var tag = _document.createElement('script');tag.async = true;tag.src = '//amplify.outbrain.com/cp/obtp.js';tag.type = 'text/javascript';var script = _document.getElementsByTagName('script')[0];script.parentNode.insertBefore(tag, script);}(window, document);
obApi('track', '${this.outbrainLandrEvent}');
`;
    },
outbrainSerp() {
    this.outbrainSerpResult = `
!function(_window, _document) {
var OB_ADV_ID='${this.pixelID}';
if (_window.obApi) {var toArray = function(object) {return Object.prototype.toString.call(object) === '[object Array]' ? object : [object];};_window.obApi.marketerId = toArray(_window.obApi.marketerId).concat(toArray(OB_ADV_ID));return;}
var api = _window.obApi = function() {api.dispatch ? api.dispatch.apply(api, arguments) : api.queue.push(arguments);};api.version = '1.1';api.loaded = true;api.marketerId = OB_ADV_ID;api.queue = [];var tag = _document.createElement('script');tag.async = true;tag.src = '//amplify.outbrain.com/cp/obtp.js';tag.type = 'text/javascript';var script = _document.getElementsByTagName('script')[0];script.parentNode.insertBefore(tag, script);}(window, document);
obApi('track', '${this.outbrainSerpEvent}');
`;
    },
outbrainAdclick() {
    this.outbrainAdclickResult = `
focus();
var listener = window.addEventListener("blur", function() {
active_element = document.activeElement;
if ("IFRAME" == active_element.tagName && 1 == window.location.href.includes("caf_results")) {
obApi('track', '${this.outbrainAdClickEvent}');
}
});
`;
    },
outbrainAdclickOnly() {
    this.outbrainAdclickOnlyResult = `
focus();
var listener = window.addEventListener("blur", function() {
active_element = document.activeElement;
if ("IFRAME" == active_element.tagName && 1 == window.location.href.includes("caf_results")) {
!function(_window, _document) {
var OB_ADV_ID='${this.pixelID}';
if (_window.obApi) {var toArray = function(object) {return Object.prototype.toString.call(object) === '[object Array]' ? object : [object];};_window.obApi.marketerId = toArray(_window.obApi.marketerId).concat(toArray(OB_ADV_ID));return;}
var api = _window.obApi = function() {api.dispatch ? api.dispatch.apply(api, arguments) : api.queue.push(arguments);};api.version = '1.1';api.loaded = true;api.marketerId = OB_ADV_ID;api.queue = [];var tag = _document.createElement('script');tag.async = true;tag.src = '//amplify.outbrain.com/cp/obtp.js';tag.type = 'text/javascript';var script = _document.getElementsByTagName('script')[0];script.parentNode.insertBefore(tag, script);}(window, document);
obApi('track', '${this.outbrainAdClickEvent}');

}
});`;
    },
// Google Tag Manager
gtmLander() {
this.gtmLandrResult = `
$.when($.getScript('https://www.googletagmanager.com/gtag/js?id=AW-395705606'),
$.Deferred(function( deferred ){
    $(deferred.resolve);
})
).done(function(){
window.dataLayer = window.dataLayer || []; 
function gtag(){dataLayer.push(arguments);} 
gtag('js', new Date()); 
gtag('config', 'AW-395705606');
});`
    },
gtmSerp() {
        this.gtmSerpResult = `
$.when($.getScript('https://www.googletagmanager.com/gtag/js?id=AW-395705606'),
$.Deferred(function( deferred ){
    $(deferred.resolve);
})
).done(function(){
window.dataLayer = window.dataLayer || []; 
function gtag(){dataLayer.push(arguments);} 
gtag('js', new Date()); 
gtag('config', 'AW-395705606');
});`
    },
firePostback() {
    this.postbackResult = `
var img = document.createElement("img"); 
img.src = "${this.postbackURL}";
img.style.display = 'none';
document.body.appendChild(img);`;
this.fireAdClickPostback();
        },
fireAdClickPostback() {
    this.adClickPostbackResult = `
focus();
var listener = window.addEventListener("blur", function() {
active_element = document.activeElement;
if ("IFRAME" == active_element.tagName && 1 == window.location.href.includes("caf_results")) {
var img = document.createElement("img"); 
img.src = "${this.postbackURL}";
img.style.display = 'none';
document.body.appendChild(img);
}
});`;
    },
copyPostback() {
    const text = this.$refs.postbackref.innerText;
    navigator.clipboard.writeText(text)
        .then(() => {
            this.copiedPostback = true;
        })
        .catch((error) => {
            alert("Failed to copy text " + error);
        });
        }
    },
    components: {  }
}
</script>

<style>
.select-column {
    border: 3px solid gray;
}

.landr {
    width: 20px;
}

.textarea {
    overflow: auto;
}

.landrTextArea {
    height: 330px;
    width: 300px;
    overflow: auto;
}

.serpTextArea {
    height: 380px;
    width: 300px;
    overflow: auto;
}

.pixel-text {
    font-size: small;
    white-space: pre;
    font-family: monospace;
}

.max-col-width {
    max-width: 600px;
}

.copied-text {
    opacity: 1;
    transition: opacity 0.5s ease-out;
}
</style>
