<html lang="ja"><head><script src="https://apis.google.com/_/scs/abc-static/_/js/k=gapi.lb.ja.M6fNbLCQVLg.O/m=gapi_iframes/rt=j/sv=1/d=1/ed=1/rs=AHpOoo96l1cuFrlaq6TmC7Jq8ZoVR-DaiA/cb=gapi.loaded_0?le=scs" async=""></script><script data-bard-client-injected="true">(function(firebaseConfig, initialAuthToken, appId) {
        window.__firebase_config = firebaseConfig;
        window.__initial_auth_token = initialAuthToken;
        window.__app_id = appId;
            })("\n{\n  \"apiKey\": \"AIzaSyCqyCcs2R2e7AegGjvFAwG98wlamtbHvZY\",\n  \"authDomain\": \"bard-frontend.firebaseapp.com\",\n  \"projectId\": \"bard-frontend\",\n  \"storageBucket\": \"bard-frontend.firebasestorage.app\",\n  \"messagingSenderId\": \"175205271074\",\n  \"appId\": \"1:175205271074:web:2b7bd4d34d33bf38e6ec7b\"\n}\n","eyJhbGciOiJSUzI1NiIsImtpZCI6IjExNjRiNzdiNDMzZDdhMDAyMWI4NjE4YjhjYTU3ZTMyZGI5MWUxMTMiLCJ0eXAiOiJKV1QifQ.eyJzdWIiOiJmaXJlYmFzZS1hZG1pbnNkay1mYnN2Y0BiYXJkLWZyb250ZW5kLmlhbS5nc2VydmljZWFjY291bnQuY29tIiwiYXVkIjoiaHR0cHM6Ly9pZGVudGl0eXRvb2xraXQuZ29vZ2xlYXBpcy5jb20vZ29vZ2xlLmlkZW50aXR5LmlkZW50aXR5dG9vbGtpdC52MS5JZGVudGl0eVRvb2xraXQiLCJ1aWQiOiIwNDY3MzMzMDA5MzExMzQwODE1NCIsImlzcyI6ImZpcmViYXNlLWFkbWluc2RrLWZic3ZjQGJhcmQtZnJvbnRlbmQuaWFtLmdzZXJ2aWNlYWNjb3VudC5jb20iLCJjbGFpbXMiOnsiYXBwSWQiOiJjXzk4ODFhZWM0ZTRlNzAxMTBfaW5kZXguaHRtbC03MSJ9LCJleHAiOjE3OTE3MjQyNTEsImlhdCI6MTc5MTcyMDY1MSwiYWxnIjoiUlMyNTYifQ.MCLKQfHKHBW9Mc0wAMWpBBazUC0nEcgFR8OwPijYXxi7qjQCc40Y06N89qUqj51HBoj1z_XVzr2FCO5w_ZjeQRglk1S6PU4Hdzes-GSWx9p4Twltn_ZFTEjJSGP7iUcfsbfUPEvByvildenNsSzR3hLAJB07SjATl_opLJTm-fn3JYDmXx4Szgatu1Nmwe5rl-kFuUK3odWvAWOIXBWPtcbhouEq2XBWMusIkiP25VBH4YhW0aeMmhx6EIiaI7wQa51oT-O2ACIQnJsBJSWCtF8aAyMCikPttCOeTdL6BuTXwF17lQ-B8ksh5nM9fbZ4HG3688A8XstgpDL8K2cX4w","c_9881aec4e4e70110_index.html-71")</script><script data-bard-client-injected="true">
  document.addEventListener('input', (event) => {
    if (event.target && (event.target.isContentEditable || event.target.hasAttribute('contenteditable'))) {
      const clonedDoc = document.cloneNode(true);
      const injectedScripts = clonedDoc.querySelectorAll('[data-bard-client-injected="true"]');
      injectedScripts.forEach(el => el.remove());
      window.parent.postMessage({
        type: 'inlineEdit',
        html: '<!DOCTYPE html>\n' + clonedDoc.documentElement.outerHTML
      }, '*');
    }
  });
</script><script data-bard-client-injected="true">(function(){'use strict';window.addEventListener("message",a=>{a.data&&a.data.type==="SUPPLEMENTAL_DATA_UPDATE"&&window.dispatchEvent(new CustomEvent("supplementaldataupdate",{detail:a.data.data}))});}).call(this);
</script><script data-bard-client-injected="true">(function() {
  const SCROLL_KEYS = new Set([
    'ArrowUp', 'ArrowDown', 'ArrowLeft', 'ArrowRight',
    ' ', 'Spacebar', 'PageUp', 'PageDown', 'Home', 'End',
  ]);
  const HORIZONTAL_KEYS = new Set(['ArrowLeft', 'ArrowRight']);

  function isTextEntryTarget(target) {
    if (!target) return false;
    const tagName = target.tagName;
    return tagName === 'INPUT' || tagName === 'TEXTAREA' ||
        tagName === 'SELECT' || target.isContentEditable === true;
  }

  // An element absorbs the key only if it both overflows on the axis being
  // scrolled and is configured to scroll on that axis. The cheap dimension
  // test runs first because getComputedStyle forces a style recalc, and this
  // runs on every keypress. Each axis is read from its own longhand: the
  // 'overflow' shorthand serializes as two values when the axes differ, which
  // is the common 'overflow-x: hidden; overflow-y: auto' pane.
  function canScroll(node, horizontal) {
    const overflows = horizontal ? node.scrollWidth > node.clientWidth
                                 : node.scrollHeight > node.clientHeight;
    if (!overflows) return false;
    const style = window.getComputedStyle(node);
    const overflow = horizontal ? style.overflowX : style.overflowY;
    return overflow === 'auto' || overflow === 'scroll';
  }

  // Walks up from the event target so nested scrollers keep their behavior.
  // <body> is included because pages that pin the root height make it the
  // scroll container.
  function hasScrollableAncestor(target, horizontal) {
    let node = target;
    while (node && node !== document.documentElement) {
      if (canScroll(node, horizontal)) return true;
      node = node.parentElement;
    }
    return false;
  }

  function rootCanScroll(horizontal) {
    const scroller = document.scrollingElement || document.documentElement;
    if (!scroller) return false;
    // Tolerate a pixel of rounding so subpixel layouts do not look scrollable.
    return horizontal ? scroller.scrollWidth > window.innerWidth + 1
                      : scroller.scrollHeight > window.innerHeight + 1;
  }

  window.addEventListener('keydown', function(event) {
    if (!SCROLL_KEYS.has(event.key)) return;
    if (event.defaultPrevented) return;
    // Alt and Meta turn arrows into browser history navigation, and Ctrl is
    // reserved for shortcuts, so none of them are scroll intent.
    if (event.altKey || event.metaKey || event.ctrlKey) return;

    const target = event.target;
    if (isTextEntryTarget(target)) return;

    // Anything that can still absorb the scroll gets to keep it.
    const horizontal = HORIZONTAL_KEYS.has(event.key);
    if (rootCanScroll(horizontal)) return;
    if (hasScrollableAncestor(target, horizontal)) return;

    event.preventDefault();
  }, {capture: true, passive: false});
})();</script><script data-bard-client-injected="true">(function() {
  // Ensure this script is executed only once
  if (window.firebaseAuthBridgeScriptLoaded) {
    return;
  }
  window.firebaseAuthBridgeScriptLoaded = true;

  let nextTokenPromiseId = 0;

  // Stores { resolve, reject } for ongoing token requests
  const pendingTokenPromises = {};

  // Listen for messages from the Host Application
  window.addEventListener('message', function(event) {

    const messageData = event.data;

  if (messageData && messageData.type === 'RESOLVE_NEW_FIREBASE_TOKEN') {
      const { success, token, error, promiseId } = messageData ?? {};
      if (pendingTokenPromises[promiseId]) {
        if (success) {
          pendingTokenPromises[promiseId].resolve(token);
        } else {
          pendingTokenPromises[promiseId].reject(new Error(error || 'Token refresh failed from host.'));
        }
        delete pendingTokenPromises[promiseId];
      }
    }
  });

  // Expose a function for the Generated App to request a new Firebase token
  window.requestNewFirebaseToken = function() {
    const currentPromiseId = nextTokenPromiseId++;
    const promise = new Promise((resolve, reject) => {
      pendingTokenPromises[currentPromiseId] = { resolve, reject };
    });
    if (window.parent && window.parent !== window) {
      window.parent.postMessage({
        type: 'REQUEST_NEW_FIREBASE_TOKEN',
        promiseId: currentPromiseId
      }, '*');
    } else {
      pendingTokenPromises[currentPromiseId].reject(new Error('No parent window to request token from.'));
      delete pendingTokenPromises[currentPromiseId];
    }
    return promise;
  };
})();</script><script data-bard-client-injected="true">
let realOriginalGetUserMedia = null;
if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
  realOriginalGetUserMedia = navigator.mediaDevices.getUserMedia.bind(navigator.mediaDevices);
}

(function() {
  if (navigator.mediaDevices && navigator.mediaDevices.__proto__) {
    try {
      Object.defineProperty(navigator.mediaDevices.__proto__, 'getUserMedia', {
        get: function() {
          return undefined; // Or throw an error
        },
        configurable: false
      });
    } catch (error) {
      console.error("Error defining prototype getter:", error);
    }
  }
})();

(function() {
  const pendingMediaResolvers = {};
  let nextMediaPromiseId = 0;

  function requestMediaPermissions(constraints) {
    const mediaPromiseId = nextMediaPromiseId++;
    const promise = new Promise((resolve, reject) => {
      pendingMediaResolvers[mediaPromiseId] = (granted) => {
        delete pendingMediaResolvers[mediaPromiseId];
        resolve(granted);
      };
    });

    window.parent.postMessage({
      type: 'requestMediaPermission',
      constraints: constraints,
      promiseId: mediaPromiseId,
    }, '*');

    return promise;
  }

  let originalGetUserMedia = realOriginalGetUserMedia;

  function interceptGetUserMedia() {
    if (navigator.mediaDevices) {
      Object.defineProperty(navigator.mediaDevices, 'getUserMedia', {
        value: function(constraints) {
          return requestMediaPermissions(constraints).then((granted) => {
            if (granted) {
              if (originalGetUserMedia) {
                return originalGetUserMedia(constraints);
              } else {
                throw new Error("Original getUserMedia not available.");
              }
            } else {
              throw new DOMException('Permission denied', 'NotAllowedError');
            }
          });
        },
        writable: false,
        configurable: false
      });
    }
  }

  interceptGetUserMedia();

  const observer = new MutationObserver(function(mutationsList, observer) {
    for (const mutation of mutationsList) {
      if (mutation.type === 'reconfigured' && mutation.name === 'getUserMedia' && mutation.object === navigator.mediaDevices) {
        interceptGetUserMedia();
      } else if (mutation.type === 'attributes' && mutation.attributeName === 'getUserMedia' && mutation.target === navigator.mediaDevices) {
        interceptGetUserMedia();
      } else if (mutation.type === 'childList' && mutation.addedNodes) {
        mutation.addedNodes.forEach(node => {
          if (node === navigator.mediaDevices) {
            interceptGetUserMedia();
          }
        });
      }
    }
  });

  function interceptSpeechRecognition() {
    if (!window.SpeechRecognition && !window.webkitSpeechRecognition) {
      return;
    }

    const OriginalSpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;

    const SpeechRecognitionWrapper = function(...args) {
      const recognizer = new OriginalSpeechRecognition(...args);
      const originalStart = recognizer.start.bind(recognizer);

      recognizer.start = function() {
        requestMediaPermissions({ audio: true }).then(granted => {
          if (granted) {
            originalStart();
          } else {
            const errorEvent = new SpeechRecognitionErrorEvent('error');
            errorEvent.error = 'not-allowed'; // This is the standard error for permission denial.
            recognizer.dispatchEvent(errorEvent);
          }
        });
      };

      return recognizer;
    };

    SpeechRecognitionWrapper.prototype = OriginalSpeechRecognition.prototype;
    SpeechRecognitionWrapper.prototype.constructor = SpeechRecognitionWrapper;

    if (window.SpeechRecognition) {
      window.SpeechRecognition = SpeechRecognitionWrapper;
    }
    if (window.webkitSpeechRecognition) {
      window.webkitSpeechRecognition = SpeechRecognitionWrapper;
    }
  }

  interceptSpeechRecognition();

  window.addEventListener('message', function(event) {
    if (event.data) {
      if (event.data.type === 'resolveMediaPermission') {
        const { promiseId, granted } = event.data;
        if (pendingMediaResolvers[promiseId]) {
          pendingMediaResolvers[promiseId](granted);
        }
      }
    }
  });

})();</script><script ws-interception-config="{&quot;parentOrigin&quot;:&quot;https://gemini.google.com&quot;,&quot;proxiedDomains&quot;:[]}" data-bard-client-injected="true">(function(){'use strict';var u=typeof Object.defineProperties=="function"?Object.defineProperty:function(b,d,e){if(b==Array.prototype||b==Object.prototype)return b;b[d]=e.value;return b};function v(b){b=["object"==typeof globalThis&&globalThis,b,"object"==typeof window&&window,"object"==typeof self&&self,"object"==typeof global&&global];for(var d=0;d<b.length;++d){var e=b[d];if(e&&e.Math==Math)return e}throw Error("Cannot find global object");}var w=v(this);
function y(b,d){if(d)a:{var e=w;b=b.split(".");for(var h=0;h<b.length-1;h++){var k=b[h];if(!(k in e))break a;e=e[k]}b=b[b.length-1];h=e[b];d=d(h);d!=h&&d!=null&&u(e,b,{configurable:!0,writable:!0,value:d})}}function z(b){function d(h){return b.next(h)}function e(h){return b.throw(h)}return new Promise(function(h,k){function m(n){n.done?h(n.value):Promise.resolve(n.value).then(d,e).then(m,k)}m(b.next())})}y("globalThis",function(b){return b||w});/*

 Copyright The Closure Library Authors.
 SPDX-License-Identifier: Apache-2.0
*/
function A(b,d){function e(){}e.prototype=d.prototype;b.j=d.prototype;b.prototype=new e;b.prototype.constructor=b;b.h=function(h,k,m){for(var n=Array(arguments.length-2),p=2;p<arguments.length;p++)n[p-2]=arguments[p];return d.prototype[k].apply(h,n)}};function B(b,d,e="*"){function h(a){if(typeof a==="string")return F.encode(a).buffer;if(a instanceof ArrayBuffer)return a.slice(0);if(ArrayBuffer.isView(a))return a.buffer.slice(a.byteOffset,a.byteOffset+a.byteLength);throw Error("Invalid data type");}function k(a){a=h(a);var f={type:"send",data:new Uint8Array(a)},g;(g=r)==null||g.postMessage(f,[a])}function m(){if(!r)throw Error("Data port not captured yet.");r.onmessage=a=>{if(a.data.type==="message"){a=new MessageEvent("message",{data:G.decode(a.data.data)});
let f;(f=c.onmessage)==null||f.call(c,a);c.dispatchEvent(a)}}}function n(){if(!t)throw Error("Control port not captured yet.");t.onmessage=a=>{switch(a.data.type){case "open":l=1;var f=new Event("open"),g;(g=c.onopen)==null||g.call(c,f);c.dispatchEvent(f);q.forEach(H=>{k(H)});q=[];break;case "close":g=a.data;l=3;g=new CloseEvent("close",{code:g.code,reason:g.reason,wasClean:g.wasClean});(f=c.onclose)==null||f.call(c,g);c.dispatchEvent(g);break;case "error":l=3;f=new Event("error");let x;(x=c.onerror)==
null||x.call(c,f);c.dispatchEvent(f)}}}function p(a){return z(function*(){var f=new MessageChannel;t=f.port1;var g=new MessageChannel;r=g.port1;n();m();window.parent.postMessage({type:"websocket_open",portOrdering:["control","data"],url:b,protocols:a||[],connectionId:I},e,[f.port2,g.port2])}())}var c=Reflect.construct(EventTarget,[],new.target);c.CONNECTING=0;c.OPEN=1;c.CLOSING=2;c.CLOSED=3;c.url=b;c.binaryType="arraybuffer";c.protocol="";c.i="";var l=0,t=null,r=null,q=[],F=new TextEncoder,G=new TextDecoder;
c.onopen=null;c.onmessage=null;c.onclose=null;c.onerror=null;Object.defineProperty(c,"readyState",{get:()=>l,enumerable:!0,configurable:!0});Object.defineProperty(c,"bufferedAmount",{get:()=>{var a=0;q.forEach(f=>{a+=typeof f==="string"?f.length:f.byteLength});return a},enumerable:!0,configurable:!0});var I=function(){var a;return((a=globalThis.crypto)==null?0:a.randomUUID)?globalThis.crypto.randomUUID():"xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx".replace(/[xy]/g,f=>{var g=Math.random()*16|0;return(f===
"x"?g:g&3|8).toString(16)})}();c.send=a=>{if(l===1)a instanceof Blob?a.arrayBuffer().then(f=>{k(f)}):k(a);else if(l===0)if(typeof a==="string")q.push(a);else if(a instanceof ArrayBuffer||ArrayBuffer.isView(a))q.push(h(a));else throw Error("Sending Blob is not supported before the connection is open.");else console.debug("WebSocket send called in CLOSING or CLOSED state; ignored.")};c.close=(a=1E3,f="")=>{if(l!==2&&l!==3){l=2;a={type:"close",code:a,reason:f,wasClean:a===1E3};var g;(g=t)==null||g.postMessage(a)}};
Promise.resolve().then(()=>p(d));return c}A(B,EventTarget);var C=document.currentScript,D=C==null?void 0:C.getAttribute("ws-interception-config");if(!D)throw Error("WebSocket Interceptor: Missing ws-interception-config attribute in the script tag.");var E=JSON.parse(D);if(!E.parentOrigin||typeof E.parentOrigin!=="string")throw Error("WebSocket Interceptor: Invalid parentOrigin in ws-interception-config");
(function(b){var d=Object.getOwnPropertyDescriptor(window,"WebSocket");if(!d||d.writable||d.configurable)d=Object.assign(function(e,h){try{let k=(new URL(e)).hostname;if(b.proxiedDomains.some(m=>k===m||k.endsWith(`.${m}`)))return new B(e,h,b.parentOrigin)}catch(k){throw window.parent.postMessage({type:"websocket_blocked",url:e,reason:"blocked_invalid_url"},b.parentOrigin),new DOMException(`WebSocket connection to '${e}' is not allowed in Canvas.`,"SecurityError");}window.parent.postMessage({type:"websocket_blocked",
url:e,reason:"blocked_domain_not_allowlisted"},b.parentOrigin);throw new DOMException(`WebSocket connection to '${e}' is not allowed in Canvas.`,"SecurityError");},{CONNECTING:0,OPEN:1,CLOSING:2,CLOSED:3}),Object.defineProperty(window,"WebSocket",{value:d,writable:!1,configurable:!1})})({proxiedDomains:E.proxiedDomains||[],parentOrigin:E.parentOrigin});}).call(this);
</script><script data-bard-client-injected="true">(function(){'use strict';function a(){window.parent.postMessage({type:"interaction"},"*")}window.addEventListener("click",a,{capture:!0,passive:!0});window.addEventListener("touchstart",a,{capture:!0,passive:!0});window.addEventListener("keydown",a,{capture:!0,passive:!0});}).call(this);
</script><script data-bard-client-injected="true">(function() {
  const originalConsoleLog = console.log;
  const originalConsoleError = console.error;

    /**
   * Normalizes an error event or a promise rejection reason into a structured error object.
   * @param {*} errorEventOrReason The error object or reason.
   * @return {object} Structured error data { message, name, stack }.
   */
  function getErrorObject(errorEventOrReason) {
    if (errorEventOrReason instanceof Error) {
      return {
        message: errorEventOrReason.message,
        name: errorEventOrReason.name,
        stack: errorEventOrReason.stack,
      };
    }
    // Fallback for non-Error objects.
    try {
      return {
        message: JSON.stringify(errorEventOrReason),
        name: 'UnknownErrorType',
        stack: null,
      };
    } catch (e) {
      return {
        message: String(errorEventOrReason),
        name: 'UnknownErrorTypeNonStringifiable',
        stack: null,
      };
    }
  }

  /**
   * Converts an array of arguments (from log/error) into a single string.
   * Handles Error objects specially to include their message and stack.
   * @param {Array<*>} args - Arguments passed to console methods.
   * @return {string} A string representation of the arguments.
   */
  function stringifyArgs(args) {
    return args
      .map((arg) => {
        if (arg instanceof Error) {
          const {message, stack} = arg;
          return `Error: ${message}${stack ? ('\nStack: ' + stack) : ''}`;
        }
        if (typeof arg === 'object' && arg !== null) {
          try {
            return JSON.stringify(arg);
          } catch (error) {
            return '[Circular Object]';
          }
        } else {
          return String(arg);
        }
      })
      .join(' ');
  }

  console.log = function(...args) {
    const logString = stringifyArgs(args);
    window.parent.postMessage({ type: 'log', message: logString }, '*');
    originalConsoleLog.apply(console, args);
  };

  console.error = function(...args) {
    let errorData;
    if (args.length > 0 && args[0] instanceof Error) {
      const err = args[0];
      // If the first arg is an Error, capture its details.
      errorData = {
        type: 'error',
        source: 'CONSOLE_ERROR',
        ...getErrorObject(err),
        rawArgsString: stringifyArgs(args.slice(1)),
        timestamp: new Date().toISOString(),
      };
    } else {
      // If not an Error object, treat all args as a general error message.
      errorData = {
        type: 'error',
        source: 'CONSOLE_ERROR',
        message: stringifyArgs(args),
        name: 'ConsoleLoggedError',
        stack: null,
        timestamp: new Date().toISOString(),
      };
    }
    window.parent.postMessage(errorData, '*');
    originalConsoleError.apply(console, args);
  };

  // Listen for global unhandled synchronous errors.
  window.addEventListener('error', function(event) {
    const errorDetails = event.error ? getErrorObject(event.error) : {
      message: event.message,
      name: 'GlobalError',
      stack: null,
      filename: event.filename,
      lineno: event.lineno,
      colno: event.colno,
    };

    window.parent.postMessage({
      type: 'error',
      source: 'global',
      ...errorDetails,
      message: errorDetails.message || event.message,
      timestamp: new Date().toISOString(),
    }, '*');
  });

  // Listen for unhandled promise rejections (asynchronous errors).
  window.addEventListener('unhandledrejection', function(event) {
    const errorDetails = getErrorObject(event.reason);

    window.parent.postMessage({
      type: 'error',
      source: 'unhandledrejection',
      ...errorDetails,
      message: errorDetails.message || 'Unhandled Promise Rejection',
      timestamp: new Date().toISOString(),
    }, '*');
  });

})();</script>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>(25:00) Dog Focus</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600;700&amp;family=Inter:wght@400;600;700&amp;display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; }
        .font-rounded { font-family: 'Fredoka', 'Inter', sans-serif; }
        @keyframes bounce-gentle {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-8px); }
        }
        @keyframes tail-wag {
            0%, 100% { transform: rotate(0deg); }
            25% { transform: rotate(-12deg); }
            75% { transform: rotate(12deg); }
        }
        .dog-walking { animation: bounce-gentle 0.8s infinite ease-in-out; }
        .tail-wagging { animation: tail-wag 0.4s infinite ease-in-out; transform-origin: bottom center; }
    </style>
<style>*, ::before, ::after{--tw-border-spacing-x:0;--tw-border-spacing-y:0;--tw-translate-x:0;--tw-translate-y:0;--tw-rotate:0;--tw-skew-x:0;--tw-skew-y:0;--tw-scale-x:1;--tw-scale-y:1;--tw-pan-x: ;--tw-pan-y: ;--tw-pinch-zoom: ;--tw-scroll-snap-strictness:proximity;--tw-gradient-from-position: ;--tw-gradient-via-position: ;--tw-gradient-to-position: ;--tw-ordinal: ;--tw-slashed-zero: ;--tw-numeric-figure: ;--tw-numeric-spacing: ;--tw-numeric-fraction: ;--tw-ring-inset: ;--tw-ring-offset-width:0px;--tw-ring-offset-color:#fff;--tw-ring-color:rgb(59 130 246 / 0.5);--tw-ring-offset-shadow:0 0 #0000;--tw-ring-shadow:0 0 #0000;--tw-shadow:0 0 #0000;--tw-shadow-colored:0 0 #0000;--tw-blur: ;--tw-brightness: ;--tw-contrast: ;--tw-grayscale: ;--tw-hue-rotate: ;--tw-invert: ;--tw-saturate: ;--tw-sepia: ;--tw-drop-shadow: ;--tw-backdrop-blur: ;--tw-backdrop-brightness: ;--tw-backdrop-contrast: ;--tw-backdrop-grayscale: ;--tw-backdrop-hue-rotate: ;--tw-backdrop-invert: ;--tw-backdrop-opacity: ;--tw-backdrop-saturate: ;--tw-backdrop-sepia: ;--tw-contain-size: ;--tw-contain-layout: ;--tw-contain-paint: ;--tw-contain-style: }::backdrop{--tw-border-spacing-x:0;--tw-border-spacing-y:0;--tw-translate-x:0;--tw-translate-y:0;--tw-rotate:0;--tw-skew-x:0;--tw-skew-y:0;--tw-scale-x:1;--tw-scale-y:1;--tw-pan-x: ;--tw-pan-y: ;--tw-pinch-zoom: ;--tw-scroll-snap-strictness:proximity;--tw-gradient-from-position: ;--tw-gradient-via-position: ;--tw-gradient-to-position: ;--tw-ordinal: ;--tw-slashed-zero: ;--tw-numeric-figure: ;--tw-numeric-spacing: ;--tw-numeric-fraction: ;--tw-ring-inset: ;--tw-ring-offset-width:0px;--tw-ring-offset-color:#fff;--tw-ring-color:rgb(59 130 246 / 0.5);--tw-ring-offset-shadow:0 0 #0000;--tw-ring-shadow:0 0 #0000;--tw-shadow:0 0 #0000;--tw-shadow-colored:0 0 #0000;--tw-blur: ;--tw-brightness: ;--tw-contrast: ;--tw-grayscale: ;--tw-hue-rotate: ;--tw-invert: ;--tw-saturate: ;--tw-sepia: ;--tw-drop-shadow: ;--tw-backdrop-blur: ;--tw-backdrop-brightness: ;--tw-backdrop-contrast: ;--tw-backdrop-grayscale: ;--tw-backdrop-hue-rotate: ;--tw-backdrop-invert: ;--tw-backdrop-opacity: ;--tw-backdrop-saturate: ;--tw-backdrop-sepia: ;--tw-contain-size: ;--tw-contain-layout: ;--tw-contain-paint: ;--tw-contain-style: }/* ! tailwindcss v3.4.17 | MIT License | https://tailwindcss.com */*,::after,::before{box-sizing:border-box;border-width:0;border-style:solid;border-color:#e5e7eb}::after,::before{--tw-content:''}:host,html{line-height:1.5;-webkit-text-size-adjust:100%;-moz-tab-size:4;tab-size:4;font-family:ui-sans-serif, system-ui, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";font-feature-settings:normal;font-variation-settings:normal;-webkit-tap-highlight-color:transparent}body{margin:0;line-height:inherit}hr{height:0;color:inherit;border-top-width:1px}abbr:where([title]){-webkit-text-decoration:underline dotted;text-decoration:underline dotted}h1,h2,h3,h4,h5,h6{font-size:inherit;font-weight:inherit}a{color:inherit;text-decoration:inherit}b,strong{font-weight:bolder}code,kbd,pre,samp{font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;font-feature-settings:normal;font-variation-settings:normal;font-size:1em}small{font-size:80%}sub,sup{font-size:75%;line-height:0;position:relative;vertical-align:baseline}sub{bottom:-.25em}sup{top:-.5em}table{text-indent:0;border-color:inherit;border-collapse:collapse}button,input,optgroup,select,textarea{font-family:inherit;font-feature-settings:inherit;font-variation-settings:inherit;font-size:100%;font-weight:inherit;line-height:inherit;letter-spacing:inherit;color:inherit;margin:0;padding:0}button,select{text-transform:none}button,input:where([type=button]),input:where([type=reset]),input:where([type=submit]){-webkit-appearance:button;background-color:transparent;background-image:none}:-moz-focusring{outline:auto}:-moz-ui-invalid{box-shadow:none}progress{vertical-align:baseline}::-webkit-inner-spin-button,::-webkit-outer-spin-button{height:auto}[type=search]{-webkit-appearance:textfield;outline-offset:-2px}::-webkit-search-decoration{-webkit-appearance:none}::-webkit-file-upload-button{-webkit-appearance:button;font:inherit}summary{display:list-item}blockquote,dd,dl,figure,h1,h2,h3,h4,h5,h6,hr,p,pre{margin:0}fieldset{margin:0;padding:0}legend{padding:0}menu,ol,ul{list-style:none;margin:0;padding:0}dialog{padding:0}textarea{resize:vertical}input::placeholder,textarea::placeholder{opacity:1;color:#9ca3af}[role=button],button{cursor:pointer}:disabled{cursor:default}audio,canvas,embed,iframe,img,object,svg,video{display:block;vertical-align:middle}img,video{max-width:100%;height:auto}[hidden]:where(:not([hidden=until-found])){display:none}.pointer-events-none{pointer-events:none}.fixed{position:fixed}.absolute{position:absolute}.relative{position:relative}.inset-0{inset:0px}.-top-1{top:-0.25rem}.bottom-5{bottom:1.25rem}.left-0{left:0px}.right-0{right:0px}.right-5{right:1.25rem}.z-10{z-index:10}.z-50{z-index:50}.col-span-2{grid-column:span 2 / span 2}.mx-3{margin-left:0.75rem;margin-right:0.75rem}.mx-auto{margin-left:auto;margin-right:auto}.-mt-1{margin-top:-0.25rem}.mb-1{margin-bottom:0.25rem}.mb-2{margin-bottom:0.5rem}.mb-3{margin-bottom:0.75rem}.mb-4{margin-bottom:1rem}.mb-5{margin-bottom:1.25rem}.mb-6{margin-bottom:1.5rem}.mt-1{margin-top:0.25rem}.mt-2{margin-top:0.5rem}.mt-6{margin-top:1.5rem}.block{display:block}.inline-block{display:inline-block}.flex{display:flex}.grid{display:grid}.hidden{display:none}.h-10{height:2.5rem}.h-3{height:0.75rem}.h-48{height:12rem}.h-full{height:100%}.max-h-48{max-height:12rem}.max-h-72{max-height:18rem}.min-h-\[140px\]{min-height:140px}.min-h-screen{min-height:100vh}.w-0{width:0px}.w-10{width:2.5rem}.w-16{width:4rem}.w-36{width:9rem}.w-48{width:12rem}.w-full{width:100%}.max-w-5xl{max-width:64rem}.max-w-md{max-width:28rem}.flex-1{flex:1 1 0%}.flex-shrink{flex-shrink:1}.flex-grow{flex-grow:1}.-translate-x-1\/2{--tw-translate-x:-50%;transform:translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}.translate-x-1\/2{--tw-translate-x:50%;transform:translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}.translate-y-5{--tw-translate-y:1.25rem;transform:translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}.-rotate-90{--tw-rotate:-90deg;transform:translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}@keyframes bounce{0%, 100%{transform:translateY(-25%);animation-timing-function:cubic-bezier(0.8,0,1,1)}50%{transform:none;animation-timing-function:cubic-bezier(0,0,0.2,1)}}.animate-bounce{animation:bounce 1s infinite}.grid-cols-1{grid-template-columns:repeat(1, minmax(0, 1fr))}.grid-cols-2{grid-template-columns:repeat(2, minmax(0, 1fr))}.flex-col{flex-direction:column}.flex-wrap{flex-wrap:wrap}.items-start{align-items:flex-start}.items-center{align-items:center}.justify-end{justify-content:flex-end}.justify-center{justify-content:center}.justify-between{justify-content:space-between}.gap-1{gap:0.25rem}.gap-1\.5{gap:0.375rem}.gap-2{gap:0.5rem}.gap-2\.5{gap:0.625rem}.gap-3{gap:0.75rem}.gap-4{gap:1rem}.gap-6{gap:1.5rem}.gap-8{gap:2rem}.space-y-2 > :not([hidden]) ~ :not([hidden]){--tw-space-y-reverse:0;margin-top:calc(0.5rem * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(0.5rem * var(--tw-space-y-reverse))}.space-y-4 > :not([hidden]) ~ :not([hidden]){--tw-space-y-reverse:0;margin-top:calc(1rem * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(1rem * var(--tw-space-y-reverse))}.divide-y > :not([hidden]) ~ :not([hidden]){--tw-divide-y-reverse:0;border-top-width:calc(1px * calc(1 - var(--tw-divide-y-reverse)));border-bottom-width:calc(1px * var(--tw-divide-y-reverse))}.divide-slate-800 > :not([hidden]) ~ :not([hidden]){--tw-divide-opacity:1;border-color:rgb(30 41 59 / var(--tw-divide-opacity, 1))}.overflow-hidden{overflow:hidden}.overflow-x-auto{overflow-x:auto}.overflow-y-auto{overflow-y:auto}.rounded{border-radius:0.25rem}.rounded-2xl{border-radius:1rem}.rounded-3xl{border-radius:1.5rem}.rounded-full{border-radius:9999px}.rounded-xl{border-radius:0.75rem}.border{border-width:1px}.border-4{border-width:4px}.border-b{border-bottom-width:1px}.border-t{border-top-width:1px}.border-amber-500{--tw-border-opacity:1;border-color:rgb(245 158 11 / var(--tw-border-opacity, 1))}.border-amber-500\/20{border-color:rgb(245 158 11 / 0.2)}.border-amber-500\/30{border-color:rgb(245 158 11 / 0.3)}.border-amber-500\/40{border-color:rgb(245 158 11 / 0.4)}.border-amber-500\/50{border-color:rgb(245 158 11 / 0.5)}.border-amber-800\/30{border-color:rgb(146 64 14 / 0.3)}.border-amber-800\/50{border-color:rgb(146 64 14 / 0.5)}.border-amber-900\/30{border-color:rgb(120 53 15 / 0.3)}.border-amber-900\/40{border-color:rgb(120 53 15 / 0.4)}.border-amber-900\/50{border-color:rgb(120 53 15 / 0.5)}.border-amber-950\/50{border-color:rgb(69 26 3 / 0.5)}.border-emerald-500\/20{border-color:rgb(16 185 129 / 0.2)}.border-orange-500\/20{border-color:rgb(249 115 22 / 0.2)}.border-slate-600{--tw-border-opacity:1;border-color:rgb(71 85 105 / var(--tw-border-opacity, 1))}.border-slate-700{--tw-border-opacity:1;border-color:rgb(51 65 85 / var(--tw-border-opacity, 1))}.border-slate-700\/50{border-color:rgb(51 65 85 / 0.5)}.border-slate-700\/60{border-color:rgb(51 65 85 / 0.6)}.border-slate-800{--tw-border-opacity:1;border-color:rgb(30 41 59 / var(--tw-border-opacity, 1))}.bg-amber-500\/10{background-color:rgb(245 158 11 / 0.1)}.bg-amber-500\/20{background-color:rgb(245 158 11 / 0.2)}.bg-amber-600{--tw-bg-opacity:1;background-color:rgb(217 119 6 / var(--tw-bg-opacity, 1))}.bg-amber-600\/20{background-color:rgb(217 119 6 / 0.2)}.bg-amber-950{--tw-bg-opacity:1;background-color:rgb(69 26 3 / var(--tw-bg-opacity, 1))}.bg-amber-950\/20{background-color:rgb(69 26 3 / 0.2)}.bg-amber-950\/30{background-color:rgb(69 26 3 / 0.3)}.bg-amber-950\/80{background-color:rgb(69 26 3 / 0.8)}.bg-black\/70{background-color:rgb(0 0 0 / 0.7)}.bg-emerald-500\/10{background-color:rgb(16 185 129 / 0.1)}.bg-orange-500\/10{background-color:rgb(249 115 22 / 0.1)}.bg-slate-700\/60{background-color:rgb(51 65 85 / 0.6)}.bg-slate-800{--tw-bg-opacity:1;background-color:rgb(30 41 59 / var(--tw-bg-opacity, 1))}.bg-slate-800\/50{background-color:rgb(30 41 59 / 0.5)}.bg-slate-800\/80{background-color:rgb(30 41 59 / 0.8)}.bg-slate-900{--tw-bg-opacity:1;background-color:rgb(15 23 42 / var(--tw-bg-opacity, 1))}.bg-slate-900\/60{background-color:rgb(15 23 42 / 0.6)}.bg-slate-900\/80{background-color:rgb(15 23 42 / 0.8)}.bg-slate-900\/90{background-color:rgb(15 23 42 / 0.9)}.bg-gradient-to-br{background-image:linear-gradient(to bottom right, var(--tw-gradient-stops))}.bg-gradient-to-r{background-image:linear-gradient(to right, var(--tw-gradient-stops))}.from-amber-400{--tw-gradient-from:#fbbf24 var(--tw-gradient-from-position);--tw-gradient-to:rgb(251 191 36 / 0) var(--tw-gradient-to-position);--tw-gradient-stops:var(--tw-gradient-from), var(--tw-gradient-to)}.from-amber-500{--tw-gradient-from:#f59e0b var(--tw-gradient-from-position);--tw-gradient-to:rgb(245 158 11 / 0) var(--tw-gradient-to-position);--tw-gradient-stops:var(--tw-gradient-from), var(--tw-gradient-to)}.from-amber-600{--tw-gradient-from:#d97706 var(--tw-gradient-from-position);--tw-gradient-to:rgb(217 119 6 / 0) var(--tw-gradient-to-position);--tw-gradient-stops:var(--tw-gradient-from), var(--tw-gradient-to)}.from-slate-900{--tw-gradient-from:#0f172a var(--tw-gradient-from-position);--tw-gradient-to:rgb(15 23 42 / 0) var(--tw-gradient-to-position);--tw-gradient-stops:var(--tw-gradient-from), var(--tw-gradient-to)}.via-amber-950\/30{--tw-gradient-to:rgb(69 26 3 / 0)  var(--tw-gradient-to-position);--tw-gradient-stops:var(--tw-gradient-from), rgb(69 26 3 / 0.3) var(--tw-gradient-via-position), var(--tw-gradient-to)}.to-orange-400{--tw-gradient-to:#fb923c var(--tw-gradient-to-position)}.to-orange-600{--tw-gradient-to:#ea580c var(--tw-gradient-to-position)}.to-slate-900{--tw-gradient-to:#0f172a var(--tw-gradient-to-position)}.bg-clip-text{-webkit-background-clip:text;background-clip:text}.p-1\.5{padding:0.375rem}.p-2\.5{padding:0.625rem}.p-3{padding:0.75rem}.p-4{padding:1rem}.p-5{padding:1.25rem}.p-6{padding:1.5rem}.px-1{padding-left:0.25rem;padding-right:0.25rem}.px-2{padding-left:0.5rem;padding-right:0.5rem}.px-3{padding-left:0.75rem;padding-right:0.75rem}.px-3\.5{padding-left:0.875rem;padding-right:0.875rem}.px-4{padding-left:1rem;padding-right:1rem}.px-5{padding-left:1.25rem;padding-right:1.25rem}.py-0\.5{padding-top:0.125rem;padding-bottom:0.125rem}.py-1{padding-top:0.25rem;padding-bottom:0.25rem}.py-1\.5{padding-top:0.375rem;padding-bottom:0.375rem}.py-2{padding-top:0.5rem;padding-bottom:0.5rem}.py-2\.5{padding-top:0.625rem;padding-bottom:0.625rem}.py-3{padding-top:0.75rem;padding-bottom:0.75rem}.py-4{padding-top:1rem;padding-bottom:1rem}.py-6{padding-top:1.5rem;padding-bottom:1.5rem}.pr-1{padding-right:0.25rem}.text-left{text-align:left}.text-center{text-align:center}.text-right{text-align:right}.font-mono{font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace}.text-2xl{font-size:1.5rem;line-height:2rem}.text-3xl{font-size:1.875rem;line-height:2.25rem}.text-4xl{font-size:2.25rem;line-height:2.5rem}.text-\[10px\]{font-size:10px}.text-base{font-size:1rem;line-height:1.5rem}.text-lg{font-size:1.125rem;line-height:1.75rem}.text-sm{font-size:0.875rem;line-height:1.25rem}.text-xl{font-size:1.25rem;line-height:1.75rem}.text-xs{font-size:0.75rem;line-height:1rem}.font-bold{font-weight:700}.font-extrabold{font-weight:800}.font-medium{font-weight:500}.font-normal{font-weight:400}.font-semibold{font-weight:600}.uppercase{text-transform:uppercase}.tracking-tight{letter-spacing:-0.025em}.tracking-wide{letter-spacing:0.025em}.tracking-widest{letter-spacing:0.1em}.text-amber-100{--tw-text-opacity:1;color:rgb(254 243 199 / var(--tw-text-opacity, 1))}.text-amber-200{--tw-text-opacity:1;color:rgb(253 230 138 / var(--tw-text-opacity, 1))}.text-amber-200\/60{color:rgb(253 230 138 / 0.6)}.text-amber-200\/80{color:rgb(253 230 138 / 0.8)}.text-amber-300{--tw-text-opacity:1;color:rgb(252 211 77 / var(--tw-text-opacity, 1))}.text-amber-300\/70{color:rgb(252 211 77 / 0.7)}.text-amber-400{--tw-text-opacity:1;color:rgb(251 191 36 / var(--tw-text-opacity, 1))}.text-amber-400\/60{color:rgb(251 191 36 / 0.6)}.text-amber-400\/80{color:rgb(251 191 36 / 0.8)}.text-amber-500{--tw-text-opacity:1;color:rgb(245 158 11 / var(--tw-text-opacity, 1))}.text-emerald-400{--tw-text-opacity:1;color:rgb(52 211 153 / var(--tw-text-opacity, 1))}.text-orange-400{--tw-text-opacity:1;color:rgb(251 146 60 / var(--tw-text-opacity, 1))}.text-slate-100{--tw-text-opacity:1;color:rgb(241 245 249 / var(--tw-text-opacity, 1))}.text-slate-200{--tw-text-opacity:1;color:rgb(226 232 240 / var(--tw-text-opacity, 1))}.text-slate-300{--tw-text-opacity:1;color:rgb(203 213 225 / var(--tw-text-opacity, 1))}.text-slate-400{--tw-text-opacity:1;color:rgb(148 163 184 / var(--tw-text-opacity, 1))}.text-slate-500{--tw-text-opacity:1;color:rgb(100 116 139 / var(--tw-text-opacity, 1))}.text-slate-800{--tw-text-opacity:1;color:rgb(30 41 59 / var(--tw-text-opacity, 1))}.text-transparent{color:transparent}.text-white{--tw-text-opacity:1;color:rgb(255 255 255 / var(--tw-text-opacity, 1))}.opacity-0{opacity:0}.shadow-2xl{--tw-shadow:0 25px 50px -12px rgb(0 0 0 / 0.25);--tw-shadow-colored:0 25px 50px -12px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-inner{--tw-shadow:inset 0 2px 4px 0 rgb(0 0 0 / 0.05);--tw-shadow-colored:inset 0 2px 4px 0 var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-lg{--tw-shadow:0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);--tw-shadow-colored:0 10px 15px -3px var(--tw-shadow-color), 0 4px 6px -4px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-md{--tw-shadow:0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);--tw-shadow-colored:0 4px 6px -1px var(--tw-shadow-color), 0 2px 4px -2px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-sm{--tw-shadow:0 1px 2px 0 rgb(0 0 0 / 0.05);--tw-shadow-colored:0 1px 2px 0 var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-xl{--tw-shadow:0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);--tw-shadow-colored:0 20px 25px -5px var(--tw-shadow-color), 0 8px 10px -6px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-orange-950\/40{--tw-shadow-color:rgb(67 20 7 / 0.4);--tw-shadow:var(--tw-shadow-colored)}.drop-shadow{--tw-drop-shadow:drop-shadow(0 1px 2px rgb(0 0 0 / 0.1)) drop-shadow(0 1px 1px rgb(0 0 0 / 0.06));filter:var(--tw-blur) var(--tw-brightness) var(--tw-contrast) var(--tw-grayscale) var(--tw-hue-rotate) var(--tw-invert) var(--tw-saturate) var(--tw-sepia) var(--tw-drop-shadow)}.drop-shadow-md{--tw-drop-shadow:drop-shadow(0 4px 3px rgb(0 0 0 / 0.07)) drop-shadow(0 2px 2px rgb(0 0 0 / 0.06));filter:var(--tw-blur) var(--tw-brightness) var(--tw-contrast) var(--tw-grayscale) var(--tw-hue-rotate) var(--tw-invert) var(--tw-saturate) var(--tw-sepia) var(--tw-drop-shadow)}.filter{filter:var(--tw-blur) var(--tw-brightness) var(--tw-contrast) var(--tw-grayscale) var(--tw-hue-rotate) var(--tw-invert) var(--tw-saturate) var(--tw-sepia) var(--tw-drop-shadow)}.backdrop-blur-md{--tw-backdrop-blur:blur(12px);-webkit-backdrop-filter:var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);backdrop-filter:var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia)}.backdrop-blur-sm{--tw-backdrop-blur:blur(4px);-webkit-backdrop-filter:var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);backdrop-filter:var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia)}.transition-all{transition-property:all;transition-timing-function:cubic-bezier(0.4, 0, 0.2, 1);transition-duration:150ms}.transition-colors{transition-property:color, background-color, border-color, fill, stroke, -webkit-text-decoration-color;transition-property:color, background-color, border-color, text-decoration-color, fill, stroke;transition-property:color, background-color, border-color, text-decoration-color, fill, stroke, -webkit-text-decoration-color;transition-timing-function:cubic-bezier(0.4, 0, 0.2, 1);transition-duration:150ms}.duration-200{transition-duration:200ms}.duration-300{transition-duration:300ms}.duration-500{transition-duration:500ms}.ease-linear{transition-timing-function:linear}.hover\:bg-amber-500:hover{--tw-bg-opacity:1;background-color:rgb(245 158 11 / var(--tw-bg-opacity, 1))}.hover\:bg-amber-500\/30:hover{background-color:rgb(245 158 11 / 0.3)}.hover\:bg-amber-600\/30:hover{background-color:rgb(217 119 6 / 0.3)}.hover\:bg-slate-700:hover{--tw-bg-opacity:1;background-color:rgb(51 65 85 / var(--tw-bg-opacity, 1))}.hover\:bg-slate-700\/80:hover{background-color:rgb(51 65 85 / 0.8)}.hover\:from-amber-500:hover{--tw-gradient-from:#f59e0b var(--tw-gradient-from-position);--tw-gradient-to:rgb(245 158 11 / 0) var(--tw-gradient-to-position);--tw-gradient-stops:var(--tw-gradient-from), var(--tw-gradient-to)}.hover\:to-orange-500:hover{--tw-gradient-to:#f97316 var(--tw-gradient-to-position)}.hover\:text-amber-300:hover{--tw-text-opacity:1;color:rgb(252 211 77 / var(--tw-text-opacity, 1))}.hover\:text-rose-400:hover{--tw-text-opacity:1;color:rgb(251 113 133 / var(--tw-text-opacity, 1))}.hover\:text-white:hover{--tw-text-opacity:1;color:rgb(255 255 255 / var(--tw-text-opacity, 1))}.focus\:border-amber-400:focus{--tw-border-opacity:1;border-color:rgb(251 191 36 / var(--tw-border-opacity, 1))}.focus\:border-amber-500:focus{--tw-border-opacity:1;border-color:rgb(245 158 11 / var(--tw-border-opacity, 1))}.focus\:outline-none:focus{outline:2px solid transparent;outline-offset:2px}.active\:scale-95:active{--tw-scale-x:.95;--tw-scale-y:.95;transform:translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}@media (min-width: 640px){.sm\:col-span-1{grid-column:span 1 / span 1}.sm\:h-56{height:14rem}.sm\:w-56{width:14rem}.sm\:grid-cols-3{grid-template-columns:repeat(3, minmax(0, 1fr))}.sm\:flex-row{flex-direction:row}.sm\:text-5xl{font-size:3rem;line-height:1}.sm\:text-sm{font-size:0.875rem;line-height:1.25rem}}@media (min-width: 768px){.md\:grid-cols-2{grid-template-columns:repeat(2, minmax(0, 1fr))}}@media (min-width: 1024px){.lg\:col-span-2{grid-column:span 2 / span 2}.lg\:grid-cols-3{grid-template-columns:repeat(3, minmax(0, 1fr))}}</style><script src="https://apis.google.com/js/api.js?onload=__iframefcb149281" type="text/javascript" charset="UTF-8" gapi_processed="true"></script></head>
<body class="bg-amber-950/20 bg-gradient-to-br from-slate-900 via-amber-950/30 to-slate-900 text-slate-100 min-h-screen flex flex-col justify-between transition-colors duration-500" id="body">

    <header class="w-full max-w-5xl mx-auto p-4 border-b border-amber-900/30 flex flex-wrap justify-between items-center gap-4">
        <div class="flex items-center gap-2.5">
            <span class="text-3xl tail-wagging inline-block">🐶</span>
            <div>
                <h1 class="text-xl font-bold tracking-wide font-rounded bg-gradient-to-r from-amber-400 to-orange-400 bg-clip-text text-transparent">
                    Dog Focus Studio
                </h1>
                <p class="text-[10px] text-amber-200/60 -mt-1">ワンちゃんと一緒に集中おべんきょう</p>
            </div>
        </div>

        <div class="flex items-center gap-3 flex-wrap">
            <button onclick="copyAllCode()" class="text-xs bg-amber-500/20 hover:bg-amber-500/30 text-amber-300 px-3 py-1.5 rounded-full border border-amber-500/40 transition-all flex items-center gap-1.5 shadow-sm">
                <i class="fa-solid fa-code"></i>
                <span>📋 コードをコピー</span>
            </button>

            <div id="room-tag" class="hidden text-xs bg-amber-950/80 text-amber-300 px-3 py-1.5 rounded-full border border-amber-500/30 flex items-center gap-2">
                <span>🏠 ルームID: <strong id="current-room-id-display" class="font-mono text-amber-200">------</strong></span>
                <button onclick="copyRoomId()" title="IDをコピー" class="hover:text-white"><i class="fa-regular fa-copy"></i></button>
                <button onclick="leaveRoom()" title="ルームを退出" class="hover:text-rose-400 text-slate-400"><i class="fa-solid fa-right-from-bracket"></i></button>
            </div>

            <button onclick="openProfileModal()" class="flex items-center gap-2 text-xs bg-slate-800/80 hover:bg-slate-700/80 text-amber-200 px-3 py-1.5 rounded-full border border-amber-900/40 transition-colors shadow-sm">
                <span id="user-avatar-display" class="text-sm">🐶</span>
                <span id="user-name-display" class="font-medium">いぬ好き</span>
                <i class="fa-solid fa-pen text-[10px] text-amber-400/60"></i>
            </button>

            <button onclick="openRoomModal()" class="text-xs bg-gradient-to-r from-amber-600 to-orange-600 hover:from-amber-500 hover:to-orange-500 text-white font-medium px-3.5 py-1.5 rounded-full shadow-md transition-all flex items-center gap-1.5">
                <i class="fa-solid fa-paw"></i>
                <span>チーム作成 / 参加</span>
            </button>
        </div>
    </header>

    <main class="w-full max-w-5xl mx-auto px-4 py-6 flex flex-col gap-8 flex-grow">
        <div class="grid grid-cols-2 sm:grid-cols-3 gap-3">
            <div class="bg-amber-950/30 p-3 rounded-2xl border border-amber-800/30 flex items-center gap-3 backdrop-blur-sm">
                <div class="w-10 h-10 rounded-xl bg-amber-500/10 border border-amber-500/20 flex items-center justify-center text-amber-400 text-xl">
                    🦴
                </div>
                <div>
                    <div class="text-[10px] text-amber-300/70">ゲットしたおやつ</div>
                    <div class="text-lg font-bold text-amber-400 font-rounded"><span id="completed-count">0</span> <span class="text-xs font-normal text-slate-400">個</span></div>
                </div>
            </div>
            <div class="bg-amber-950/30 p-3 rounded-2xl border border-amber-800/30 flex items-center gap-3 backdrop-blur-sm">
                <div class="w-10 h-10 rounded-xl bg-emerald-500/10 border border-emerald-500/20 flex items-center justify-center text-emerald-400 text-xl">
                    ⏱️
                </div>
                <div>
                    <div class="text-[10px] text-slate-400">個人集中時間</div>
                    <div class="text-lg font-bold text-emerald-400 font-rounded"><span id="total-study-time">0</span> <span class="text-xs font-normal text-slate-400">分</span></div>
                </div>
            </div>
            <div class="col-span-2 sm:col-span-1 bg-amber-950/30 p-3 rounded-2xl border border-amber-800/30 flex items-center gap-3 backdrop-blur-sm">
                <div class="w-10 h-10 rounded-xl bg-orange-500/10 border border-orange-500/20 flex items-center justify-center text-orange-400 text-xl">
                    🏆
                </div>
                <div>
                    <div class="text-[10px] text-slate-400">チーム合計時間</div>
                    <div class="text-lg font-bold text-orange-400 font-rounded"><span id="team-study-time">0</span> <span class="text-xs font-normal text-slate-400">分</span></div>
                </div>
            </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 items-start">
            <div class="flex flex-col items-center bg-slate-800/50 p-6 rounded-3xl border border-amber-900/30 backdrop-blur-md shadow-xl relative overflow-hidden">
                <div class="flex flex-col sm:flex-row bg-slate-900/80 p-1.5 rounded-2xl w-full mb-4 border border-slate-700/50 shadow-inner gap-1">
                    <div class="flex flex-1 gap-1">
                        <button onclick="setTimerPreset('pomodoro', 25)" id="tab-pomodoro" class="flex-1 py-2 text-xs sm:text-sm font-semibold rounded-xl transition-all duration-200 bg-amber-600 text-white shadow-md">
                            🐕 集中 (25分)
                        </button>
                        <button onclick="setTimerPreset('shortBreak', 5)" id="tab-shortBreak" class="flex-1 py-2 text-xs sm:text-sm font-semibold rounded-xl transition-all duration-200 text-slate-400 hover:text-white">
                            ☕ 小休憩 (5分)
                        </button>
                    </div>
                    <div class="flex flex-1 gap-1">
                        <button onclick="setTimerPreset('longBreak', 15)" id="tab-longBreak" class="flex-1 py-2 text-xs sm:text-sm font-semibold rounded-xl transition-all duration-200 text-slate-400 hover:text-white">
                            🎾 長休憩 (15分)
                        </button>
                        <button onclick="toggleCustomInput()" id="tab-custom" class="flex-1 py-2 text-xs sm:text-sm font-semibold rounded-xl transition-all duration-200 text-amber-400 hover:text-amber-300 border border-amber-500/30 bg-amber-500/10">
                            ⚙️ 自由設定
                        </button>
                    </div>
                </div>

                <div id="custom-time-box" class="hidden w-full bg-slate-900/90 p-3 rounded-2xl mb-4 border border-amber-500/40 flex items-center justify-between gap-3 shadow-inner">
                    <div class="flex items-center gap-2">
                        <span class="text-xs text-amber-300 font-semibold">⏱️ 好きな時間を設定:</span>
                        <input type="number" id="custom-minutes-input" min="1" max="180" value="30" class="w-16 bg-slate-800 border border-amber-500/50 rounded-xl px-2 py-1 text-center font-mono text-sm text-white focus:outline-none focus:border-amber-400">
                        <span class="text-xs text-slate-300">分</span>
                    </div>
                    <button onclick="applyCustomTime()" class="bg-amber-600 hover:bg-amber-500 text-white text-xs px-3 py-1.5 rounded-xl font-bold shadow-md transition-all">
                        セット
                    </button>
                </div>

                <div class="w-full bg-slate-900/60 rounded-2xl p-4 mb-5 border border-amber-950/50 flex flex-col items-center justify-between min-h-[140px] relative">
                    <div class="w-full flex justify-between items-center text-xs text-amber-200/80 mb-2 font-medium px-1">
                        <span id="dog-status-text">ワンちゃんがおやつに向かって前進中！</span>
                        <span id="treats-remaining-badge" class="bg-amber-950 text-amber-400 border border-amber-800/50 px-2 py-0.5 rounded-full font-mono text-[10px]">🦴 30分達成でおやつ1個獲得</span>
                    </div>

                    <div class="w-full relative py-3">
                        <div class="w-full h-3 bg-slate-800 rounded-full overflow-hidden border border-slate-700">
                            <div id="dog-progress-fill" class="h-full bg-gradient-to-r from-amber-500 to-orange-400 transition-all duration-500 w-0" style="width: 0%;"></div>
                        </div>

                        <div id="dog-runner" class="absolute -top-1 left-0 transition-all duration-500 -translate-x-1/2 flex flex-col items-center" style="left: 0%;">
                            <span id="dog-emoji" class="text-3xl filter drop-shadow">🐶</span>
                        </div>

                        <div class="absolute -top-1 right-0 translate-x-1/2 flex flex-col items-center">
                            <span id="goal-emoji" class="text-2xl animate-bounce">🦴</span>
                        </div>
                    </div>

                    <div id="dog-treats-container" class="flex gap-1.5 mt-2 flex-wrap justify-center text-lg"></div>
                </div>

                <div class="relative w-48 h-48 sm:w-56 sm:h-56 flex items-center justify-center mb-6 rounded-full bg-slate-900/90 border-4 border-amber-900/40 shadow-2xl transition-all duration-300">
                    <svg class="absolute inset-0 w-full h-full -rotate-90" viewBox="0 0 100 100">
                        <circle cx="50" cy="50" r="44" stroke="currentColor" stroke-width="4" class="text-slate-800" fill="transparent"></circle>
                        <circle id="progress-bar" cx="50" cy="50" r="44" stroke="currentColor" stroke-width="4" class="text-amber-500 transition-all duration-500 ease-linear" fill="transparent" stroke-dasharray="276.46" stroke-dashoffset="0" stroke-linecap="round" style="stroke-dashoffset: 0px;"></circle>
                    </svg>

                    <div class="text-center z-10">
                        <span id="time-display" class="text-4xl sm:text-5xl font-extrabold tracking-tight font-mono text-amber-100 drop-shadow-md">25:00</span>
                        <p id="mode-label" class="text-[10px] text-amber-400/80 mt-1 uppercase tracking-widest font-semibold font-rounded">Focus Time</p>
                    </div>
                </div>

                <div class="flex items-center gap-4">
                    <button id="start-btn" onclick="toggleTimer()" class="w-36 py-3 bg-gradient-to-r from-amber-600 to-orange-600 hover:from-amber-500 hover:to-orange-500 active:scale-95 text-white font-bold rounded-2xl shadow-lg shadow-orange-950/40 transition-all duration-200 flex items-center justify-center gap-2">
                        <i class="fa-solid fa-play" id="start-icon"></i>
                        <span id="start-text">スタート</span>
                    </button>
                    <button onclick="resetTimer()" class="p-3 bg-slate-800 hover:bg-slate-700 active:scale-95 text-slate-300 rounded-2xl border border-slate-700 transition-all duration-200" title="リセット">
                        <i class="fa-solid fa-rotate-right"></i>
                    </button>
                </div>
            </div>

            <div class="flex flex-col gap-4">
                <div class="bg-slate-800/50 backdrop-blur-sm border border-slate-700/60 rounded-3xl p-5 shadow-lg">
                    <h2 class="text-sm font-semibold text-slate-300 mb-3 flex items-center justify-between">
                        <span class="flex items-center gap-2"><i class="fa-solid fa-bone text-amber-400"></i> ワンちゃんと攻略するタスク</span>
                        <span class="text-xs text-amber-300/70 font-mono">おやつ獲得条件</span>
                    </h2>
                    <div class="flex gap-2 mb-3">
                        <input type="text" id="task-input" placeholder="例: 数学ドリル P.12まで" class="flex-1 bg-slate-900 border border-slate-700 rounded-xl px-3 py-2 text-sm text-slate-200 focus:outline-none focus:border-amber-500 transition-colors">
                        <button onclick="addTask()" class="bg-amber-600 hover:bg-amber-500 text-white px-4 py-2 rounded-xl text-sm font-medium transition-colors">
                            追加
                        </button>
                    </div>
                    <ul id="task-list" class="space-y-2 max-h-48 overflow-y-auto pr-1">
                    </ul>
                </div>

                <div class="bg-slate-800/50 backdrop-blur-sm border border-slate-700/60 rounded-3xl p-4 shadow-lg">
                    <label class="text-xs font-semibold text-slate-400 block mb-2">現在の勉強科目</label>
                    <div class="flex flex-wrap gap-2" id="subject-tags">
                        <button onclick="selectSubject('数学')" class="subject-tag text-xs px-3 py-1.5 rounded-xl border border-amber-500/50 bg-amber-500/20 text-amber-300 font-medium">数学</button>
                        <button onclick="selectSubject('英語')" class="subject-tag text-xs px-3 py-1.5 rounded-xl border border-slate-700 bg-slate-800 text-slate-400">英語</button>
                        <button onclick="selectSubject('国語')" class="subject-tag text-xs px-3 py-1.5 rounded-xl border border-slate-700 bg-slate-800 text-slate-400">国語</button>
                        <button onclick="selectSubject('理科')" class="subject-tag text-xs px-3 py-1.5 rounded-xl border border-slate-700 bg-slate-800 text-slate-400">理科</button>
                        <button onclick="selectSubject('社会')" class="subject-tag text-xs px-3 py-1.5 rounded-xl border border-slate-700 bg-slate-800 text-slate-400">社会</button>
                        <button onclick="selectSubject('プログラミング')" class="subject-tag text-xs px-3 py-1.5 rounded-xl border border-slate-700 bg-slate-800 text-slate-400">プログラミング</button>
                        <button onclick="selectSubject('その他')" class="subject-tag text-xs px-3 py-1.5 rounded-xl border border-slate-700 bg-slate-800 text-slate-400">その他</button>
                    </div>
                </div>
            </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
            <div class="lg:col-span-2 bg-slate-800/50 border border-slate-700/60 rounded-3xl p-5 shadow-lg flex flex-col">
                <div class="flex justify-between items-center mb-4">
                    <h2 class="text-base font-semibold text-slate-200 flex items-center gap-2">
                        <i class="fa-solid fa-clock-rotate-left text-amber-400"></i> 学習履歴テーブル
                    </h2>
                    <span class="text-xs text-slate-500">あなたのワンちゃんのお散歩記録</span>
                </div>
                <div class="overflow-x-auto flex-grow">
                    <table class="w-full text-left text-sm text-slate-300">
                        <thead class="text-xs text-slate-400 bg-slate-900/60 uppercase border-b border-slate-700">
                            <tr>
                                <th class="py-2.5 px-3">日時</th>
                                <th class="py-2.5 px-3">科目</th>
                                <th class="py-2.5 px-3">内容 / タスク</th>
                                <th class="py-2.5 px-3 text-right">集中時間</th>
                            </tr>
                        </thead>
                        <tbody id="logs-table-body" class="divide-y divide-slate-800"><tr><td colspan="4" class="text-center py-6 text-xs text-slate-500">まだ学習記録がありません。タイマーを完了するとここに記録されます！</td></tr></tbody>
                    </table>
                </div>
            </div>

            <div class="bg-slate-800/50 border border-slate-700/60 rounded-3xl p-5 shadow-lg flex flex-col">
                <div class="flex justify-between items-center mb-3">
                    <h2 class="text-base font-semibold text-slate-200 flex items-center gap-2">
                        <i class="fa-solid fa-trophy text-amber-400"></i> <span id="ranking-title">わんわんチーム対戦</span>
                    </h2>
                    <span id="room-status-badge" class="text-[10px] bg-slate-700/60 text-slate-300 border border-slate-600 px-2 py-0.5 rounded">ソロお散歩</span>
                </div>
                <p class="text-xs text-slate-400 mb-3" id="ranking-subtitle">ルームを作成して友達のワンちゃんと勉強時間勝負！</p>
                
                <div class="space-y-2 flex-grow overflow-y-auto max-h-72 pr-1" id="ranking-list">
                </div>
            </div>
        </div>

    </main>

    <div id="profile-modal" class="fixed inset-0 bg-black/70 backdrop-blur-sm hidden items-center justify-center z-50 p-4">
        <div class="bg-slate-800 border border-amber-900/50 rounded-3xl p-6 w-full max-w-md shadow-2xl">
            <h3 class="text-lg font-bold text-white mb-4 flex items-center gap-2 font-rounded">
                <span>🐶</span> 相棒ワンちゃん＆プロフィール設定
            </h3>
            
            <div class="mb-4">
                <label class="block text-xs font-semibold text-slate-400 mb-1">ニックネーム</label>
                <input type="text" id="input-username" maxlength="15" placeholder="名前を入力" class="w-full bg-slate-900 border border-slate-700 rounded-xl px-3 py-2.5 text-sm text-slate-100 focus:outline-none focus:border-amber-500">
            </div>

            <div class="mb-6">
                <label class="block text-xs font-semibold text-slate-400 mb-2">相棒ワンちゃんを選択</label>
                <div class="flex gap-2 flex-wrap" id="avatar-selector">
                    <button onclick="selectAvatar('🐶')" class="avatar-opt text-2xl p-2.5 rounded-2xl bg-slate-900 border border-amber-500">🐶</button>
                    <button onclick="selectAvatar('🐕')" class="avatar-opt text-2xl p-2.5 rounded-2xl bg-slate-900 border border-slate-700">🐕</button>
                    <button onclick="selectAvatar('🦮')" class="avatar-opt text-2xl p-2.5 rounded-2xl bg-slate-900 border border-slate-700">🦮</button>
                    <button onclick="selectAvatar('🐕‍🦺')" class="avatar-opt text-2xl p-2.5 rounded-2xl bg-slate-900 border border-slate-700">🐕‍🦺</button>
                    <button onclick="selectAvatar('🐩')" class="avatar-opt text-2xl p-2.5 rounded-2xl bg-slate-900 border border-slate-700">🐩</button>
                    <button onclick="selectAvatar('🐾')" class="avatar-opt text-2xl p-2.5 rounded-2xl bg-slate-900 border border-slate-700">🐾</button>
                </div>
            </div>

            <div class="flex justify-end gap-3">
                <button onclick="closeProfileModal()" class="px-4 py-2 text-xs font-medium text-slate-400 hover:text-white">キャンセル</button>
                <button onclick="saveProfile()" class="px-5 py-2 text-xs font-semibold bg-amber-600 hover:bg-amber-500 text-white rounded-xl shadow-lg">保存する</button>
            </div>
        </div>
    </div>

    <div id="room-modal" class="fixed inset-0 bg-black/70 backdrop-blur-sm hidden items-center justify-center z-50 p-4">
        <div class="bg-slate-800 border border-amber-900/50 rounded-3xl p-6 w-full max-w-md shadow-2xl">
            <h3 class="text-lg font-bold text-white mb-2 flex items-center gap-2 font-rounded">
                <i class="fa-solid fa-paw text-amber-400"></i> チーム（愛犬クラブ）対戦
            </h3>
            <p class="text-xs text-slate-400 mb-6">同じIDを入力した仲間同士でワンちゃんの勉強時間をリアルタイムで競い合えます！</p>

            <div class="space-y-4">
                <div class="bg-slate-900/80 p-4 rounded-2xl border border-slate-700/60">
                    <label class="block text-xs font-semibold text-amber-300 mb-2">部屋のID（ルームID）を入力</label>
                    <div class="flex gap-2">
                        <input type="text" id="input-room-id" placeholder="例: DOGPUPPY" class="flex-1 uppercase font-mono bg-slate-800 border border-slate-700 rounded-xl px-3 py-2 text-sm text-slate-100 focus:outline-none focus:border-amber-500">
                        <button onclick="joinRoomByInput()" class="bg-amber-600 hover:bg-amber-500 text-white px-4 py-2 rounded-xl text-xs font-semibold transition-colors">
                            参加する
                        </button>
                    </div>
                </div>

                <div class="relative flex py-1 items-center">
                    <div class="flex-grow border-t border-slate-700"></div>
                    <span class="flex-shrink mx-3 text-[10px] text-slate-500 uppercase">または</span>
                    <div class="flex-grow border-t border-slate-700"></div>
                </div>

                <button onclick="createNewRoom()" class="w-full py-3 bg-amber-600/20 hover:bg-amber-600/30 border border-amber-500/40 text-amber-200 font-semibold rounded-2xl text-xs flex items-center justify-center gap-2 transition-all">
                    <i class="fa-solid fa-plus-circle text-amber-400"></i> 新しいワンちゃんチームを自動作成
                </button>
            </div>

            <div class="mt-6 flex justify-end">
                <button onclick="closeRoomModal()" class="px-4 py-2 text-xs font-medium text-slate-400 hover:text-white">閉じる</button>
            </div>
        </div>
    </div>

    <div id="toast" class="fixed bottom-5 right-5 bg-slate-800 border border-amber-500/50 text-amber-200 text-xs px-4 py-3 rounded-2xl shadow-xl transition-all duration-300 opacity-0 translate-y-5 pointer-events-none z-50 flex items-center gap-2">
        <span class="text-base">🐶</span>
        <span id="toast-message">通知メッセージ</span>
    </div>

    <footer class="w-full text-center py-4 text-xs text-slate-500 border-t border-slate-800">
        <p>Dog Focus Studio - ワンちゃんと楽しく集中タイマー</p>
    </footer>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, setDoc, getDoc, collection, onSnapshot } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        const appId = typeof __app_id !== 'undefined' ? __app_id : 'dog-focus-app';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {
            apiKey: "demo", authDomain: "demo.firebaseapp.com", projectId: "demo", storageBucket: "demo.appspot.com"
        };

        const app = initializeApp(firebaseConfig);
        const auth = getAuth(app);
        const db = getFirestore(app);

        let currentUser = null;
        let userId = null;
        let userName = localStorage.getItem('dog_username') || 'いぬ好き ' + Math.floor(100 + Math.random() * 900);
        let userAvatar = localStorage.getItem('dog_useravatar') || '🐶';
        let currentRoomId = localStorage.getItem('dog_roomid') || null;

        let timer = null;
        let isRunning = false;
        let activeTimerMode = 'pomodoro';
        let totalDuration = 25 * 60;
        let timeRemaining = totalDuration;
        let completedSessions = parseInt(localStorage.getItem('dog_treat_count') || '0', 10);
        let totalStudyMinutes = parseInt(localStorage.getItem('dog_total_mins') || '0', 10);
        let selectedSubject = '数学';
        
        let studyLogs = [];
        let roomUnsubscribe = null;

        const modeConfigs = {
            pomodoro: { label: 'Focus Time', color: 'text-amber-500', bgBtn: 'bg-amber-600', goalEmoji: '🦴' },
            shortBreak: { label: 'Short Break', color: 'text-emerald-500', bgBtn: 'bg-emerald-600', goalEmoji: '☕' },
            longBreak: { label: 'Long Break', color: 'text-sky-500', bgBtn: 'bg-sky-600', goalEmoji: '🎾' },
            custom: { label: 'Custom Focus', color: 'text-orange-500', bgBtn: 'bg-orange-600', goalEmoji: '🦴' }
        };

        const timeDisplay = document.getElementById('time-display');
        const modeLabelText = document.getElementById('mode-label');
        const startBtn = document.getElementById('start-btn');
        const startIcon = document.getElementById('start-icon');
        const startText = document.getElementById('start-text');
        const progressBar = document.getElementById('progress-bar');

        async function initAuth() {
            try {
                if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                    await signInWithCustomToken(auth, __initial_auth_token);
                } else {
                    await signInAnonymously(auth);
                }
            } catch (err) {
                console.error("Auth initialization failed:", err);
            }
        }

        onAuthStateChanged(auth, async (user) => {
            if (user) {
                currentUser = user;
                userId = user.uid;
                updateProfileUI();

                if (currentRoomId) {
                    joinRoom(currentRoomId);
                } else {
                    renderSoloRanking();
                }
            }
        });

        initAuth();

        window.showToast = function(msg) {
            const toast = document.getElementById('toast');
            document.getElementById('toast-message').textContent = msg;
            toast.classList.remove('opacity-0', 'translate-y-5', 'pointer-events-none');
            setTimeout(() => {
                toast.classList.add('opacity-0', 'translate-y-5', 'pointer-events-none');
            }, 3000);
        }

        window.copyAllCode = function() {
            const htmlContent = document.documentElement.outerHTML;
            const tempTextarea = document.createElement('textarea');
            tempTextarea.value = htmlContent;
            document.body.appendChild(tempTextarea);
            tempTextarea.select();
            document.execCommand('copy');
            document.body.removeChild(tempTextarea);
            window.showToast('📋 ソロコードをすべてコピーしました！ index.html に保存してください');
        }

        window.openProfileModal = function() {
            document.getElementById('input-username').value = userName;
            document.getElementById('profile-modal').classList.remove('hidden');
            document.getElementById('profile-modal').classList.add('flex');
        }

        window.closeProfileModal = function() {
            document.getElementById('profile-modal').classList.add('hidden');
            document.getElementById('profile-modal').classList.remove('flex');
        }

        window.selectAvatar = function(emoji) {
            userAvatar = emoji;
            document.getElementById('dog-emoji').textContent = emoji;
            const buttons = document.querySelectorAll('.avatar-opt');
            buttons.forEach(btn => {
                if (btn.textContent.trim() === emoji) {
                    btn.className = 'avatar-opt text-2xl p-2.5 rounded-2xl bg-slate-900 border border-amber-500';
                } else {
                    btn.className = 'avatar-opt text-2xl p-2.5 rounded-2xl bg-slate-900 border border-slate-700';
                }
            });
        }

        window.saveProfile = function() {
            const newName = document.getElementById('input-username').value.trim();
            if (newName) userName = newName;
            
            localStorage.setItem('dog_username', userName);
            localStorage.setItem('dog_useravatar', userAvatar);
            
            updateProfileUI();
            syncUserDataToRoom();
            closeProfileModal();
            showToast('プロフィールを保存しました！');
        }

        function updateProfileUI() {
            document.getElementById('user-name-display').textContent = userName;
            document.getElementById('user-avatar-display').textContent = userAvatar;
            document.getElementById('dog-emoji').textContent = userAvatar;
            document.getElementById('completed-count').textContent = completedSessions;
            renderTreats();
        }

        function renderTreats() {
            const container = document.getElementById('dog-treats-container');
            container.innerHTML = '';
            const maxShow = Math.min(completedSessions, 10);
            for (let i = 0; i < maxShow; i++) {
                const span = document.createElement('span');
                span.textContent = '🦴';
                span.className = 'animate-bounce';
                span.style.animationDelay = `${i * 0.1}s`;
                container.appendChild(span);
            }
            if (completedSessions > 10) {
                const extra = document.createElement('span');
                extra.className = 'text-xs text-amber-400 font-bold self-center ml-1 font-mono';
                extra.textContent = `+${completedSessions - 10}`;
                container.appendChild(extra);
            }
        }

        window.openRoomModal = function() {
            document.getElementById('room-modal').classList.remove('hidden');
            document.getElementById('room-modal').classList.add('flex');
        }

        window.closeRoomModal = function() {
            document.getElementById('room-modal').classList.add('hidden');
            document.getElementById('room-modal').classList.remove('flex');
        }

        window.createNewRoom = function() {
            const newId = Math.random().toString(36).substring(2, 8).toUpperCase();
            joinRoom(newId);
            closeRoomModal();
        }

        window.joinRoomByInput = function() {
            const inputId = document.getElementById('input-room-id').value.trim().toUpperCase();
            if (!inputId) return;
            joinRoom(inputId);
            closeRoomModal();
        }

        async function joinRoom(roomId) {
            if (!currentUser) return;
            
            if (roomUnsubscribe) {
                roomUnsubscribe();
                roomUnsubscribe = null;
            }

            currentRoomId = roomId;
            localStorage.setItem('dog_roomid', roomId);

            document.getElementById('room-tag').classList.remove('hidden');
            document.getElementById('room-tag').classList.add('flex');
            document.getElementById('current-room-id-display').textContent = roomId;
            document.getElementById('ranking-title').textContent = `愛犬チーム (${roomId})`;
            document.getElementById('ranking-subtitle').textContent = `ID「${roomId}」のメンバーとわんわん勉強対戦中！`;
            document.getElementById('room-status-badge').textContent = 'リアルタイム対戦';
            document.getElementById('room-status-badge').className = 'text-[10px] bg-amber-500/20 text-amber-300 border border-amber-500/30 px-2 py-0.5 rounded';

            await syncUserDataToRoom();

            const roomDataRef = collection(db, 'artifacts', appId, 'public', 'data', `room_${roomId}`);
            
            roomUnsubscribe = onSnapshot(roomDataRef, (snapshot) => {
                const members = [];
                let totalTeamMins = 0;

                snapshot.forEach(docSnap => {
                    const data = docSnap.data();
                    members.push(data);
                    totalTeamMins += (data.minutes || 0);
                });

                document.getElementById('team-study-time').textContent = totalTeamMins;
                renderRoomRanking(members);
            }, (error) => {
                console.error("Firestore error:", error);
            });

            showToast(`チーム「${roomId}」に参加しました！`);
        }

        async function syncUserDataToRoom() {
            if (!currentUser || !currentRoomId) return;

            const memberRef = doc(db, 'artifacts', appId, 'public', 'data', `room_${currentRoomId}`, userId);
            try {
                await setDoc(memberRef, {
                    uid: userId,
                    name: userName,
                    avatar: userAvatar,
                    minutes: totalStudyMinutes,
                    treats: completedSessions,
                    updatedAt: Date.now()
                }, { merge: true });
            } catch (err) {
                console.error("Error syncing user data:", err);
            }
        }

        window.leaveRoom = function() {
            if (roomUnsubscribe) {
                roomUnsubscribe();
                roomUnsubscribe = null;
            }

            currentRoomId = null;
            localStorage.removeItem('dog_roomid');

            document.getElementById('room-tag').classList.add('hidden');
            document.getElementById('room-tag').classList.remove('flex');
            document.getElementById('ranking-title').textContent = 'わんわんチーム対戦';
            document.getElementById('ranking-subtitle').textContent = 'チームに参加して友達と勉強時間を競い合おう！';
            document.getElementById('room-status-badge').textContent = 'ソロお散歩';
            document.getElementById('room-status-badge').className = 'text-[10px] bg-slate-700/60 text-slate-300 border border-slate-600 px-2 py-0.5 rounded';
            document.getElementById('team-study-time').textContent = totalStudyMinutes;

            renderSoloRanking();
            showToast('チームを退出しました。');
        }

        window.copyRoomId = function() {
            if (!currentRoomId) return;
            const tempInput = document.createElement('input');
            tempInput.value = currentRoomId;
            document.body.appendChild(tempInput);
            tempInput.select();
            document.execCommand('copy');
            document.body.removeChild(tempInput);
            showToast(`ID: ${currentRoomId} をコピーしました！`);
        }

        function renderRoomRanking(members) {
            const list = document.getElementById('ranking-list');
            list.innerHTML = '';

            members.sort((a, b) => (b.minutes || 0) - (a.minutes || 0));

            members.forEach((item, index) => {
                const isUser = item.uid === userId;
                const div = document.createElement('div');
                div.className = `flex items-center justify-between p-2.5 rounded-2xl border text-xs transition-all ${
                    isUser 
                        ? 'bg-amber-600/20 border-amber-500/50 text-amber-200 font-semibold shadow-sm' 
                        : 'bg-slate-900/60 border-slate-800 text-slate-300'
                }`;

                let rankBadge = `<span class="w-5 font-bold text-slate-400">${index + 1}</span>`;
                if (index === 0) rankBadge = `<span class="w-5 text-amber-400 font-extrabold">🥇</span>`;
                if (index === 1) rankBadge = `<span class="w-5 text-slate-300 font-extrabold">🥈</span>`;
                if (index === 2) rankBadge = `<span class="w-5 text-amber-600 font-extrabold">🥉</span>`;

                div.innerHTML = `
                    <div class="flex items-center gap-2">
                        ${rankBadge}
                        <span class="text-lg">${item.avatar || '🐶'}</span>
                        <span class="truncate max-w-[110px]">${escapeHtml(item.name || 'メンバー')} ${isUser ? '(あなた)' : ''}</span>
                    </div>
                    <div class="flex items-center gap-2">
                        <span class="text-[10px] text-amber-400">🦴 ${item.treats || 0}</span>
                        <span class="font-mono text-xs ${isUser ? 'text-amber-300 font-bold' : 'text-slate-400'}">${item.minutes || 0} 分</span>
                    </div>
                `;
                list.appendChild(div);
            });
        }

        function renderSoloRanking() {
            const list = document.getElementById('ranking-list');
            list.innerHTML = '';

            const mockData = [
                { name: userName + ' (あなた)', avatar: userAvatar, minutes: totalStudyMinutes, treats: completedSessions, isUser: true },
                { name: 'しばいぬ丸', avatar: '🐕', minutes: 120, treats: 4, isUser: false },
                { name: 'ポメラニアン学長', avatar: '🐩', minutes: 90, treats: 3, isUser: false },
                { name: 'レトリバー先生', avatar: '🦮', minutes: 45, treats: 1, isUser: false }
            ];

            mockData.sort((a, b) => b.minutes - a.minutes);

            mockData.forEach((item, index) => {
                const div = document.createElement('div');
                div.className = `flex items-center justify-between p-2.5 rounded-2xl border text-xs transition-all ${
                    item.isUser 
                        ? 'bg-amber-600/20 border-amber-500/50 text-amber-200 font-semibold shadow-sm' 
                        : 'bg-slate-900/60 border-slate-800 text-slate-300'
                }`;

                let rankBadge = `<span class="w-5 font-bold text-slate-400">${index + 1}</span>`;
                if (index === 0) rankBadge = `<span class="w-5 text-amber-400 font-extrabold">🥇</span>`;
                if (index === 1) rankBadge = `<span class="w-5 text-slate-300 font-extrabold">🥈</span>`;
                if (index === 2) rankBadge = `<span class="w-5 text-amber-600 font-extrabold">🥉</span>`;

                div.innerHTML = `
                    <div class="flex items-center gap-2">
                        ${rankBadge}
                        <span class="text-lg">${item.avatar}</span>
                        <span class="truncate max-w-[110px]">${escapeHtml(item.name)}</span>
                    </div>
                    <div class="flex items-center gap-2">
                        <span class="text-[10px] text-amber-400">🦴 ${item.treats}</span>
                        <span class="font-mono text-xs ${item.isUser ? 'text-amber-300 font-bold' : 'text-slate-400'}">${item.minutes} 分</span>
                    </div>
                `;
                list.appendChild(div);
            });
        }

        function playBeep() {
            try {
                const ctx = new (window.AudioContext || window.webkitAudioContext)();
                const osc = ctx.createOscillator();
                const gain = ctx.createGain();
                osc.type = 'sine';
                osc.frequency.setValueAtTime(587.33, ctx.currentTime);
                osc.frequency.setValueAtTime(880, ctx.currentTime + 0.15);
                gain.gain.setValueAtTime(0.1, ctx.currentTime);
                gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + 0.6);
                osc.connect(gain);
                gain.connect(ctx.destination);
                osc.start();
                osc.stop(ctx.currentTime + 0.6);
            } catch(e) {}
        }

        function updateDisplay() {
            const minutes = Math.floor(timeRemaining / 60);
            const seconds = timeRemaining % 60;
            timeDisplay.textContent = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
            
            const circumference = 276.46;
            const offset = circumference - (timeRemaining / totalDuration) * circumference;
            progressBar.style.strokeDashoffset = offset;

            const progressPercent = Math.min(100, Math.max(0, ((totalDuration - timeRemaining) / totalDuration) * 100));
            document.getElementById('dog-progress-fill').style.width = `${progressPercent}%`;
            document.getElementById('dog-runner').style.left = `${progressPercent}%`;

            document.title = `(${minutes}:${seconds.toString().padStart(2, '0')}) Dog Focus`;
        }

        window.toggleCustomInput = function() {
            const box = document.getElementById('custom-time-box');
            box.classList.toggle('hidden');
        }

        window.applyCustomTime = function() {
            const minutesInput = parseInt(document.getElementById('custom-minutes-input').value, 10);
            if (isNaN(minutesInput) || minutesInput <= 0) return;
            
            window.setTimerPreset('custom', minutesInput);
            document.getElementById('custom-time-box').classList.add('hidden');
            showToast(`${minutesInput}分のタイマーを設定しました！`);
        }

        window.setTimerPreset = function(newMode, minutes) {
            pauseTimer();
            activeTimerMode = newMode;
            totalDuration = minutes * 60;
            timeRemaining = totalDuration;

            ['pomodoro', 'shortBreak', 'longBreak', 'custom'].forEach(m => {
                const tab = document.getElementById(`tab-${m}`);
                if (tab) {
                    if (m === activeTimerMode) {
                        tab.className = `flex-1 py-2 text-xs sm:text-sm font-semibold rounded-xl transition-all duration-200 text-white shadow-md ${modeConfigs[m].bgBtn}`;
                    } else if (m === 'custom') {
                        tab.className = 'flex-1 py-2 text-xs sm:text-sm font-semibold rounded-xl transition-all duration-200 text-amber-400 hover:text-amber-300 border border-amber-500/30 bg-amber-500/10';
                    } else {
                        tab.className = 'flex-1 py-2 text-xs sm:text-sm font-semibold rounded-xl transition-all duration-200 text-slate-400 hover:text-white';
                    }
                }
            });

            document.getElementById('goal-emoji').textContent = modeConfigs[activeTimerMode].goalEmoji;
            progressBar.className = `transition-all duration-500 ease-linear ${modeConfigs[activeTimerMode].color}`;
            modeLabelText.textContent = modeConfigs[activeTimerMode].label;

            if (activeTimerMode === 'pomodoro' || activeTimerMode === 'custom') {
                document.getElementById('dog-status-text').textContent = 'ワンちゃんがおやつに向かって前進中！';
                const earnedTreatsEstimate = Math.max(1, Math.round((minutes / 30) * 10) / 10);
                document.getElementById('treats-remaining-badge').textContent = `🦴 達成で約 ${earnedTreatsEstimate} 個のおやつ！`;
            } else {
                document.getElementById('dog-status-text').textContent = '休憩中！ワンちゃんもおやすみ中💤';
                document.getElementById('treats-remaining-badge').textContent = '☕ リフレッシュタイム';
            }

            updateDisplay();
        }

        window.toggleTimer = function() {
            if (isRunning) {
                pauseTimer();
            } else {
                startTimer();
            }
        }

        function startTimer() {
            if (isRunning) return;
            isRunning = true;
            startIcon.className = 'fa-solid fa-pause';
            startText.textContent = '一時停止';
            document.getElementById('dog-runner').classList.add('dog-walking');

            timer = setInterval(() => {
                if (timeRemaining > 0) {
                    timeRemaining--;
                    updateDisplay();
                } else {
                    timerComplete();
                }
            }, 1000);
        }

        function pauseTimer() {
            isRunning = false;
            clearInterval(timer);
            startIcon.className = 'fa-solid fa-play';
            startText.textContent = 'スタート';
            document.getElementById('dog-runner').classList.remove('dog-walking');
        }

        window.resetTimer = function() {
            pauseTimer();
            timeRemaining = totalDuration;
            updateDisplay();
        }

        window.selectSubject = function(subject) {
            selectedSubject = subject;
            const buttons = document.querySelectorAll('.subject-tag');
            buttons.forEach(btn => {
                if (btn.textContent.trim() === subject) {
                    btn.className = 'subject-tag text-xs px-3 py-1.5 rounded-xl border border-amber-500/50 bg-amber-500/20 text-amber-300 font-medium';
                } else {
                    btn.className = 'subject-tag text-xs px-3 py-1.5 rounded-xl border border-slate-700 bg-slate-800 text-slate-400';
                }
            });
        }

        function timerComplete() {
            pauseTimer();
            playBeep();

            const sessionMinutes = Math.max(1, Math.round(totalDuration / 60));

            if (activeTimerMode === 'pomodoro' || activeTimerMode === 'custom') {
                const earnedTreats = Math.max(1, Math.floor(sessionMinutes / 30) || (sessionMinutes >= 1 ? 1 : 0));
                completedSessions += earnedTreats;
                totalStudyMinutes += sessionMinutes;

                localStorage.setItem('dog_treat_count', completedSessions.toString());
                localStorage.setItem('dog_total_mins', totalStudyMinutes.toString());

                document.getElementById('completed-count').textContent = completedSessions;
                document.getElementById('total-study-time').textContent = totalStudyMinutes;

                renderTreats();
                recordStudyLog(sessionMinutes);
                syncUserDataToRoom();

                showToast(`🎉 ${sessionMinutes}分集中完了！おやつ🦴を${earnedTreats}個ゲットしました！`);
                window.setTimerPreset('shortBreak', 5);
            } else {
                showToast('⏰ 休憩終了！次の学習を開始しましょう！');
                window.setTimerPreset('pomodoro', 25);
            }
        }

        function recordStudyLog(minutes) {
            const now = new Date();
            const timeStr = `${now.getHours().toString().padStart(2, '0')}:${now.getMinutes().toString().padStart(2, '0')}`;
            
            const activeTaskInput = document.querySelector('#task-list span:not(.line-through)');
            const taskContent = activeTaskInput ? activeTaskInput.textContent : '集中学習';

            studyLogs.unshift({
                time: timeStr,
                subject: selectedSubject,
                task: taskContent,
                duration: `${minutes} 分`
            });

            renderLogs();
        }

        function renderLogs() {
            const tbody = document.getElementById('logs-table-body');
            tbody.innerHTML = '';

            if (studyLogs.length === 0) {
                tbody.innerHTML = `<tr><td colspan="4" class="text-center py-6 text-xs text-slate-500">まだ学習記録がありません。タイマーを完了するとここに記録されます！</td></tr>`;
                return;
            }

            studyLogs.forEach(log => {
                const tr = document.createElement('tr');
                tr.className = 'hover:bg-slate-800/30 transition-colors';
                tr.innerHTML = `
                    <td class="py-2.5 px-3 text-xs text-slate-400 font-mono">${log.time}</td>
                    <td class="py-2.5 px-3 text-xs"><span class="px-2 py-0.5 rounded-lg bg-amber-500/10 text-amber-400 border border-amber-500/20 font-medium">${log.subject}</span></td>
                    <td class="py-2.5 px-3 text-xs text-slate-200 truncate max-w-[150px]">${escapeHtml(log.task)}</td>
                    <td class="py-2.5 px-3 text-xs text-right font-medium text-emerald-400 font-mono">${log.duration}</td>
                `;
                tbody.appendChild(tr);
            });
        }

        window.addTask = function() {
            const input = document.getElementById('task-input');
            const taskText = input.value.trim();
            if (!taskText) return;

            const list = document.getElementById('task-list');
            const li = document.createElement('li');
            li.className = 'flex items-center justify-between bg-slate-900/80 p-2.5 rounded-xl border border-slate-700/50 text-sm';
            
            li.innerHTML = `
                <div class="flex items-center gap-2 overflow-hidden">
                    <input type="checkbox" onchange="toggleTask(this)" class="w-4 h-4 accent-amber-500 rounded cursor-pointer">
                    <span class="text-slate-200 text-xs sm:text-sm truncate">${escapeHtml(taskText)}</span>
                </div>
                <button onclick="this.parentElement.remove()" class="text-slate-500 hover:text-rose-400 p-1 transition-colors">
                    <i class="fa-solid fa-trash-can text-xs"></i>
                </button>
            `;

            list.appendChild(li);
            input.value = '';
        }

        window.toggleTask = function(checkbox) {
            const span = checkbox.nextElementSibling;
            if (checkbox.checked) {
                span.classList.add('line-through', 'text-slate-500');
            } else {
                span.classList.remove('line-through', 'text-slate-500');
            }
        }

        function escapeHtml(text) {
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }

        document.getElementById('task-input').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') addTask();
        });

        document.getElementById('total-study-time').textContent = totalStudyMinutes;
        document.getElementById('team-study-time').textContent = totalStudyMinutes;
        updateDisplay();
        renderTreats();
        renderLogs();
    </script>

<iframe ng-non-bindable="" frameborder="0" hspace="0" marginheight="0" marginwidth="0" scrolling="no" tabindex="-1" vspace="0" width="100%" aria-hidden="true" id="I0_1791720652732" name="I0_1791720652732" src="https://bard-frontend.firebaseapp.com/__/auth/iframe?apiKey=AIzaSyCqyCcs2R2e7AegGjvFAwG98wlamtbHvZY&amp;appName=%5BDEFAULT%5D&amp;v=11.6.1&amp;eid=p&amp;usegapi=1&amp;jsh=m%3B%2F_%2Fscs%2Fabc-static%2F_%2Fjs%2Fk%3Dgapi.lb.ja.M6fNbLCQVLg.O%2Fd%3D1%2Frs%3DAHpOoo96l1cuFrlaq6TmC7Jq8ZoVR-DaiA%2Fm%3D__features__#id=I0_1791720652732&amp;_gfid=I0_1791720652732&amp;parent=blob%3A%2F%2F&amp;pfname=&amp;rpctoken=21179364" style="position: absolute; top: -100px; width: 1px; height: 1px;"></iframe></body></html>
