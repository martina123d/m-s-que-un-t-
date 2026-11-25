// https://d3js.org/d3-array/ v3.2.4 Copyright 2010-2023 Mike Bostock
!function(t,n){"object"==typeof exports&&"undefined"!=typeof module?n(exports):"function"==typeof define&&define.amd?define(["exports"],n):n((t="undefined"!=typeof globalThis?globalThis:t||self).d3=t.d3||{})}(this,(function(t){"use strict";function n(t,n){return null==t||null==n?NaN:t<n?-1:t>n?1:t>=n?0:NaN}function r(t,n){return null==t||null==n?NaN:n<t?-1:n>t?1:n>=t?0:NaN}function e(t){let e,f,i;function u(t,n,r=0,o=t.length){if(r<o){if(0!==e(n,n))return o;do{const e=r+o>>>1;f(t[e],n)<0?r=e+1:o=e}while(r<o)}return r}return 2!==t.length?(e=n,f=(r,e)=>n(t(r),e),i=(n,r)=>t(n)-r):(e=t===n||t===r?t:o,f=t,i=t),{left:u,center:function(t,n,r=0,e=t.length){const o=u(t,n,r,e-1);return o>r&&i(t[o-1],n)>-i(t[o],n)?o-1:o},right:function(t,n,r=0,o=t.length){if(r<o){if(0!==e(n,n))return o;do{const e=r+o>>>1;f(t[e],n)<=0?r=e+1:o=e}while(r<o)}return r}}}function o(){return 0}function f(t){return null===t?NaN:+t}const i=e(n),u=i.right,l=i.left,c=e(f).center;var s=u;const a=d(m),h=d((function(t){const n=m(t);return(t,r,e,o,f)=>{n(t,r,(e<<=2)+0,(o<<=2)+0,f<<=2),n(t,r,e+1,o+1,f),n(t,r,e+2,o+2,f),n(t,r,e+3,o+3,f)}}));function d(t){return function(n,r,e=r){if(!((r=+r)>=0))throw new RangeError("invalid rx");if(!((e=+e)>=0))throw new RangeError("invalid ry");let{data:o,width:f,height:i}=n;if(!((f=Math.floor(f))>=0))throw new RangeError("invalid width");if(!((i=Math.floor(void 0!==i?i:o.length/f))>=0))throw new RangeError("invalid height");if(!f||!i||!r&&!e)return n;const u=r&&t(r),l=e&&t(e),c=o.slice();return u&&l?(p(u,c,o,f,i),p(u,o,c,f,i),p(u,c,o,f,i),y(l,o,c,f,i),y(l,c,o,f,i),y(l,o,c,f,i)):u?(p(u,o,c,f,i),p(u,c,o,f,i),p(u,o,c,f,i)):l&&(y(l,o,c,f,i),y(l,c,o,f,i),y(l,o,c,f,i)),n}}function p(t,n,r,e,o){for(let f=0,i=e*o;f<i;)t(n,r,f,f+=e,1)}function y(t,n,r,e,o){for(let f=0,i=e*o;f<e;++f)t(n,r,f,f+i,e)}function m(t){const n=Math.floor(t);if(n===t)return function(t){const n=2*t+1;return(r,e,o,f,i)=>{if(!((f-=i)>=o))return;let u=t*e[o];const l=i*t;for(let t=o,n=o+l;t<n;t+=i)u+=e[Math.min(f,t)];for(let t=o,c=f;t<=c;t+=i)u+=e[Math.min(f,t+l)],r[t]=u/n,u-=e[Math.max(o,t-l)]}}(t);const r=t-n,e=2*t+1;return(t,o,f,i,u)=>{if(!((i-=u)>=f))return;let l=n*o[f];const c=u*n,s=c+u;for(let t=f,n=f+c;t<n;t+=u)l+=o[Math.min(i,t)];for(let n=f,a=i;n<=a;n+=u)l+=o[Math.min(i,n+c)],t[n]=(l+r*(o[Math.max(f,n-s)]+o[Math.min(i,n+s)]))/e,l-=o[Math.max(f,n-c)]}}function g(t,n){let r=0;if(void 0===n)for(let n of t)null!=n&&(n=+n)>=n&&++r;else{let e=-1;for(let o of t)null!=(o=n(o,++e,t))&&(o=+o)>=o&&++r}return r}function v(t){return 0|t.length}function M(t){return!(t>0)}function w(t){return"object"!=typeof t||"length"in t?t:Array.from(t)}function b(t,n){let r,e=0,o=0,f=0;if(void 0===n)for(let n of t)null!=n&&(n=+n)>=n&&(r=n-o,o+=r/++e,f+=r*(n-o));else{let i=-1;for(let u of t)null!=(u=n(u,++i,t))&&(u=+u)>=u&&(r=u-o,o+=r/++e,f+=r*(u-o))}if(e>1)return f/(e-1)}function A(t,n){const r=b(t,n);return r?Math.sqrt(r):r}function x(t,n){let r,e;if(void 0===n)for(const n of t)null!=n&&(void 0===r?n>=n&&(r=e=n):(r>n&&(r=n),e<n&&(e=n)));else{let o=-1;for(let f of t)null!=(f=n(f,++o,t))&&(void 0===r?f>=f&&(r=e=f):(r>f&&(r=f),e<f&&(e=f)))}return[r,e]}class N{constructor(){this._partials=new Float64Array(32),this._n=0}add(t){const n=this._partials;let r=0;for(let e=0;e<this._n&&e<32;e++){const o=n[e],f=t+o,i=Math.abs(t)<Math.abs(o)?t-(f-o):o-(f-t);i&&(n[r++]=i),t=f}return n[r]=t,this._n=r+1,this}valueOf(){const t=this._partials;let n,r,e,o=this._n,f=0;if(o>0){for(f=t[--o];o>0&&(n=f,r=t[--o],f=n+r,e=r-(f-n),!e););o>0&&(e<0&&t[o-1]<0||e>0&&t[o-1]>0)&&(r=2*e,n=f+r,r==n-f&&(f=n))}return f}}class InternMap extends Map{constructor(t,n=k){if(super(),Object.defineProperties(this,{_intern:{value:new Map},_key:{value:n}}),null!=t)for(const[n,r]of t)this.set(n,r)}get(t){return super.get(E(this,t))}has(t){return super.has(E(this,t))}set(t,n){return super.set(_(this,t),n)}delete(t){return super.delete(S(this,t))}}class InternSet extends Set{constructor(t,n=k){if(super(),Object.defineProperties(this,{_intern:{value:new Map},_key:{value:n}}),null!=t)for(const n of t)this.add(n)}has(t){return super.has(E(this,t))}add(t){return super.add(_(this,t))}delete(t){return super.delete(S(this,t))}}function E({_intern:t,_key:n},r){const e=n(r);return t.has(e)?t.get(e):r}function _({_intern:t,_key:n},r){const e=n(r);return t.has(e)?t.get(e):(t.set(e,r),r)}function S({_intern:t,_key:n},r){const e=n(r);return t.has(e)&&(r=t.get(e),t.delete(e)),r}function k(t){return null!==t&&"object"==typeof t?t.valueOf():t}function T(t){return t}function F(t,...n){return U(t,T,T,n)}function I(t,...n){return U(t,Array.from,T,n)}function j(t,n){for(let r=1,e=n.length;r<e;++r)t=t.flatMap((t=>t.pop().map((([n,r])=>[...t,n,r]))));return t}function q(t,n,...r){return U(t,T,n,r)}function R(t,n,...r){return U(t,Array.from,n,r)}function O(t){if(1!==t.length)throw new Error("duplicate key");return t[0]}function U(t,n,r,e){return function t(o,f){if(f>=e.length)return r(o);const i=new InternMap,u=e[f++];let l=-1;for(const t of o){const n=u(t,++l,o),r=i.get(n);r?r.push(t):i.set(n,[t])}for(const[n,r]of i)i.set(n,t(r,f));return n(i)}(t,0)}function L(t,n){return Array.from(n,(n=>t[n]))}function P(t,...n){if("function"!=typeof t[Symbol.iterator])throw new TypeError("values is not iterable");t=Array.from(t);let[r]=n;if(r&&2!==r.length||n.length>1){const e=Uint32Array.from(t,((t,n)=>n));return n.length>1?(n=n.map((n=>t.map(n))),e.sort(((t,r)=>{for(const e of n){const n=C(e[t],e[r]);if(n)return n}}))):(r=t.map(r),e.sort(((t,n)=>C(r[t],r[n])))),L(t,e)}return t.sort(z(r))}function z(t=n){if(t===n)return C;if("function"!=typeof t)throw new TypeError("compare is not a function");return(n,r)=>{const e=t(n,r);return e||0===e?e:(0===t(r,r))-(0===t(n,n))}}function C(t,n){return(null==t||!(t>=t))-(null==n||!(n>=n))||(t<n?-1:t>n?1:0)}var D=Array.prototype.slice;function G(t){return()=>t}const B=Math.sqrt(50),H=Math.sqrt(10),J=Math.sqrt(2);function K(t,n,r){const e=(n-t)/Math.max(0,r),o=Math.floor(Math.log10(e)),f=e/Math.pow(10,o),i=f>=B?10:f>=H?5:f>=J?2:1;let u,l,c;return o<0?(c=Math.pow(10,-o)/i,u=Math.round(t*c),l=Math.round(n*c),u/c<t&&++u,l/c>n&&--l,c=-c):(c=Math.pow(10,o)*i,u=Math.round(t/c),l=Math.round(n/c),u*c<t&&++u,l*c>n&&--l),l<u&&.5<=r&&r<2?K(t,n,2*r):[u,l,c]}function Q(t,n,r){if(!((r=+r)>0))return[];if((t=+t)===(n=+n))return[t];const e=n<t,[o,f,i]=e?K(n,t,r):K(t,n,r);if(!(f>=o))return[];const u=f-o+1,l=new Array(u);if(e)if(i<0)for(let t=0;t<u;++t)l[t]=(f-t)/-i;else for(let t=0;t<u;++t)l[t]=(f-t)*i;else if(i<0)for(let t=0;t<u;++t)l[t]=(o+t)/-i;else for(let t=0;t<u;++t)l[t]=(o+t)*i;return l}function V(t,n,r){return K(t=+t,n=+n,r=+r)[2]}function W(t,n,r){let e;for(;;){const o=V(t,n,r);if(o===e||0===o||!isFinite(o))return[t,n];o>0?(t=Math.floor(t/o)*o,n=Math.ceil(n/o)*o):o<0&&(t=Math.ceil(t*o)/o,n=Math.floor(n*o)/o),e=o}}function X(t){return Math.max(1,Math.ceil(Math.log(g(t))/Math.LN2)+1)}function Y(){var t=T,n=x,r=X;function e(e){Array.isArray(e)||(e=Array.from(e));var o,f,i,u=e.length,l=new Array(u);for(o=0;o<u;++o)l[o]=t(e[o],o,e);var c=n(l),a=c[0],h=c[1],d=r(l,a,h);if(!Array.isArray(d)){const t=h,r=+d;if(n===x&&([a,h]=W(a,h,r)),(d=Q(a,h,r))[0]<=a&&(i=V(a,h,r)),d[d.length-1]>=h)if(t>=h&&n===x){const t=V(a,h,r);isFinite(t)&&(t>0?h=(Math.floor(h/t)+1)*t:t<0&&(h=(Math.ceil(h*-t)+1)/-t))}else d.pop()}for(var p=d.length,y=0,m=p;d[y]<=a;)++y;for(;d[m-1]>h;)--m;(y||m<p)&&(d=d.slice(y,m),p=m-y);var g,v=new Array(p+1);for(o=0;o<=p;++o)(g=v[o]=[]).x0=o>0?d[o-1]:a,g.x1=o<p?d[o]:h;if(isFinite(i)){if(i>0)for(o=0;o<u;++o)null!=(f=l[o])&&a<=f&&f<=h&&v[Math.min(p,Math.floor((f-a)/i))].push(e[o]);else if(i<0)for(o=0;o<u;++o)if(null!=(f=l[o])&&a<=f&&f<=h){const t=Math.floor((a-f)*i);v[Math.min(p,t+(d[t]<=f))].push(e[o])}}else for(o=0;o<u;++o)null!=(f=l[o])&&a<=f&&f<=h&&v[s(d,f,0,p)].push(e[o]);return v}return e.value=function(n){return arguments.length?(t="function"==typeof n?n:G(n),e):t},e.domain=function(t){return arguments.length?(n="function"==typeof t?t:G([t[0],t[1]]),e):n},e.thresholds=function(t){return arguments.length?(r="function"==typeof t?t:G(Array.isArray(t)?D.call(t):t),e):r},e}function Z(t,n){let r;if(void 0===n)for(const n of t)null!=n&&(r<n||void 0===r&&n>=n)&&(r=n);else{let e=-1;for(let o of t)null!=(o=n(o,++e,t))&&(r<o||void 0===r&&o>=o)&&(r=o)}return r}function $(t,n){let r,e=-1,o=-1;if(void 0===n)for(const n of t)++o,null!=n&&(r<n||void 0===r&&n>=n)&&(r=n,e=o);else for(let f of t)null!=(f=n(f,++o,t))&&(r<f||void 0===r&&f>=f)&&(r=f,e=o);return e}function tt(t,n){let r;if(void 0===n)for(const n of t)null!=n&&(r>n||void 0===r&&n>=n)&&(r=n);else{let e=-1;for(let o of t)null!=(o=n(o,++e,t))&&(r>o||void 0===r&&o>=o)&&(r=o)}return r}function nt(t,n){let r,e=-1,o=-1;if(void 0===n)for(const n of t)++o,null!=n&&(r>n||void 0===r&&n>=n)&&(r=n,e=o);else for(let f of t)null!=(f=n(f,++o,t))&&(r>f||void 0===r&&f>=f)&&(r=f,e=o);return e}function rt(t,n,r=0,e=1/0,o){if(n=Math.floor(n),r=Math.floor(Math.max(0,r)),e=Math.floor(Math.min(t.length-1,e)),!(r<=n&&n<=e))return t;for(o=void 0===o?C:z(o);e>r;){if(e-r>600){const f=e-r+1,i=n-r+1,u=Math.log(f),l=.5*Math.exp(2*u/3),c=.5*Math.sqrt(u*l*(f-l)/f)*(i-f/2<0?-1:1);rt(t,n,Math.max(r,Math.floor(n-i*l/f+c)),Math.min(e,Math.floor(n+(f-i)*l/f+c)),o)}const f=t[n];let i=r,u=e;for(et(t,r,n),o(t[e],f)>0&&et(t,r,e);i<u;){for(et(t,i,u),++i,--u;o(t[i],f)<0;)++i;for(;o(t[u],f)>0;)--u}0===o(t[r],f)?et(t,r,u):(++u,et(t,u,e)),u<=n&&(r=u+1),n<=u&&(e=u-1)}return t}function et(t,n,r){const e=t[n];t[n]=t[r],t[r]=e}function ot(t,r=n){let e,o=!1;if(1===r.length){let f;for(const i of t){const t=r(i);(o?n(t,f)>0:0===n(t,t))&&(e=i,f=t,o=!0)}}else for(const n of t)(o?r(n,e)>0:0===r(n,n))&&(e=n,o=!0);return e}function ft(t,n,r){if(t=Float64Array.from(function*(t,n){if(void 0===n)for(let n of t)null!=n&&(n=+n)>=n&&(yield n);else{let r=-1;for(let e of t)null!=(e=n(e,++r,t))&&(e=+e)>=e&&(yield e)}}(t,r)),(e=t.length)&&!isNaN(n=+n)){if(n<=0||e<2)return tt(t);if(n>=1)return Z(t);var e,o=(e-1)*n,f=Math.floor(o),i=Z(rt(t,f).subarray(0,f+1));return i+(tt(t.subarray(f+1))-i)*(o-f)}}function it(t,n,r=f){if(!isNaN(n=+n)){if(e=Float64Array.from(t,((n,e)=>f(r(t[e],e,t)))),n<=0)return nt(e);if(n>=1)return $(e);var e,o=Uint32Array.from(t,((t,n)=>n)),i=e.length-1,u=Math.floor(i*n);return rt(o,u,0,i,((t,n)=>C(e[t],e[n]))),(u=ot(o.subarray(0,u+1),(t=>e[t])))>=0?u:-1}}function ut(t,n){return[t,n]}function lt(t,r=n){if(1===r.length)return nt(t,r);let e,o=-1,f=-1;for(const n of t)++f,(o<0?0===r(n,n):r(n,e)<0)&&(e=n,o=f);return o}var ct=st(Math.random);function st(t){return function(n,r=0,e=n.length){let o=e-(r=+r);for(;o;){const e=t()*o--|0,f=n[o+r];n[o+r]=n[e+r],n[e+r]=f}return n}}function at(t){if(!(o=t.length))return[];for(var n=-1,r=tt(t,ht),e=new Array(r);++n<r;)for(var o,f=-1,i=e[n]=new Array(o);++f<o;)i[f]=t[f][n];return e}function ht(t){return t.length}function dt(t){return t instanceof InternSet?t:new InternSet(t)}function pt(t,n){const r=t[Symbol.iterator](),e=new Set;for(const t of n){const n=yt(t);if(e.has(n))continue;let o,f;for(;({value:o,done:f}=r.next());){if(f)return!1;const t=yt(o);if(e.add(t),Object.is(n,t))break}}return!0}function yt(t){return null!==t&&"object"==typeof t?t.valueOf():t}t.Adder=N,t.InternMap=InternMap,t.InternSet=InternSet,t.ascending=n,t.bin=Y,t.bisect=s,t.bisectCenter=c,t.bisectLeft=l,t.bisectRight=u,t.bisector=e,t.blur=function(t,n){if(!((n=+n)>=0))throw new RangeError("invalid r");let r=t.length;if(!((r=Math.floor(r))>=0))throw new RangeError("invalid length");if(!r||!n)return t;const e=m(n),o=t.slice();return e(t,o,0,r,1),e(o,t,0,r,1),e(t,o,0,r,1),t},t.blur2=a,t.blurImage=h,t.count=g,t.cross=function(...t){const n="function"==typeof t[t.length-1]&&function(t){return n=>t(...n)}(t.pop()),r=(t=t.map(w)).map(v),e=t.length-1,o=new Array(e+1).fill(0),f=[];if(e<0||r.some(M))return f;for(;;){f.push(o.map(((n,r)=>t[r][n])));let i=e;for(;++o[i]===r[i];){if(0===i)return n?f.map(n):f;o[i--]=0}}},t.cumsum=function(t,n){var r=0,e=0;return Float64Array.from(t,void 0===n?t=>r+=+t||0:o=>r+=+n(o,e++,t)||0)},t.descending=r,t.deviation=A,t.difference=function(t,...n){t=new InternSet(t);for(const r of n)for(const n of r)t.delete(n);return t},t.disjoint=function(t,n){const r=n[Symbol.iterator](),e=new InternSet;for(const n of t){if(e.has(n))return!1;let t,o;for(;({value:t,done:o}=r.next())&&!o;){if(Object.is(n,t))return!1;e.add(t)}}return!0},t.every=function(t,n){if("function"!=typeof n)throw new TypeError("test is not a function");let r=-1;for(const e of t)if(!n(e,++r,t))return!1;return!0},t.extent=x,t.fcumsum=function(t,n){const r=new N;let e=-1;return Float64Array.from(t,void 0===n?t=>r.add(+t||0):o=>r.add(+n(o,++e,t)||0))},t.filter=function(t,n){if("function"!=typeof n)throw new TypeError("test is not a function");const r=[];let e=-1;for(const o of t)n(o,++e,t)&&r.push(o);return r},t.flatGroup=function(t,...n){return j(I(t,...n),n)},t.flatRollup=function(t,n,...r){return j(R(t,n,...r),r)},t.fsum=function(t,n){const r=new N;if(void 0===n)for(let n of t)(n=+n)&&r.add(n);else{let e=-1;for(let o of t)(o=+n(o,++e,t))&&r.add(o)}return+r},t.greatest=ot,t.greatestIndex=function(t,r=n){if(1===r.length)return $(t,r);let e,o=-1,f=-1;for(const n of t)++f,(o<0?0===r(n,n):r(n,e)>0)&&(e=n,o=f);return o},t.group=F,t.groupSort=function(t,r,e){return(2!==r.length?P(q(t,r,e),(([t,r],[e,o])=>n(r,o)||n(t,e))):P(F(t,e),(([t,e],[o,f])=>r(e,f)||n(t,o)))).map((([t])=>t))},t.groups=I,t.histogram=Y,t.index=function(t,...n){return U(t,T,O,n)},t.indexes=function(t,...n){return U(t,Array.from,O,n)},t.intersection=function(t,...n){t=new InternSet(t),n=n.map(dt);t:for(const r of t)for(const e of n)if(!e.has(r)){t.delete(r);continue t}return t},t.least=function(t,r=n){let e,o=!1;if(1===r.length){let f;for(const i of t){const t=r(i);(o?n(t,f)<0:0===n(t,t))&&(e=i,f=t,o=!0)}}else for(const n of t)(o?r(n,e)<0:0===r(n,n))&&(e=n,o=!0);return e},t.leastIndex=lt,t.map=function(t,n){if("function"!=typeof t[Symbol.iterator])throw new TypeError("values is not iterable");if("function"!=typeof n)throw new TypeError("mapper is not a function");return Array.from(t,((r,e)=>n(r,e,t)))},t.max=Z,t.maxIndex=$,t.mean=function(t,n){let r=0,e=0;if(void 0===n)for(let n of t)null!=n&&(n=+n)>=n&&(++r,e+=n);else{let o=-1;for(let f of t)null!=(f=n(f,++o,t))&&(f=+f)>=f&&(++r,e+=f)}if(r)return e/r},t.median=function(t,n){return ft(t,.5,n)},t.medianIndex=function(t,n){return it(t,.5,n)},t.merge=function(t){return Array.from(function*(t){for(const n of t)yield*n}(t))},t.min=tt,t.minIndex=nt,t.mode=function(t,n){const r=new InternMap;if(void 0===n)for(let n of t)null!=n&&n>=n&&r.set(n,(r.get(n)||0)+1);else{let e=-1;for(let o of t)null!=(o=n(o,++e,t))&&o>=o&&r.set(o,(r.get(o)||0)+1)}let e,o=0;for(const[t,n]of r)n>o&&(o=n,e=t);return e},t.nice=W,t.pairs=function(t,n=ut){const r=[];let e,o=!1;for(const f of t)o&&r.push(n(e,f)),e=f,o=!0;return r},t.permute=L,t.quantile=ft,t.quantileIndex=it,t.quantileSorted=function(t,n,r=f){if((e=t.length)&&!isNaN(n=+n)){if(n<=0||e<2)return+r(t[0],0,t);if(n>=1)return+r(t[e-1],e-1,t);var e,o=(e-1)*n,i=Math.floor(o),u=+r(t[i],i,t);return u+(+r(t[i+1],i+1,t)-u)*(o-i)}},t.quickselect=rt,t.range=function(t,n,r){t=+t,n=+n,r=(o=arguments.length)<2?(n=t,t=0,1):o<3?1:+r;for(var e=-1,o=0|Math.max(0,Math.ceil((n-t)/r)),f=new Array(o);++e<o;)f[e]=t+e*r;return f},t.rank=function(t,r=n){if("function"!=typeof t[Symbol.iterator])throw new TypeError("values is not iterable");let e=Array.from(t);const o=new Float64Array(e.length);2!==r.length&&(e=e.map(r),r=n);const f=(t,n)=>r(e[t],e[n]);let i,u;return(t=Uint32Array.from(e,((t,n)=>n))).sort(r===n?(t,n)=>C(e[t],e[n]):z(f)),t.forEach(((t,n)=>{const r=f(t,void 0===i?t:i);r>=0?((void 0===i||r>0)&&(i=t,u=n),o[t]=u):o[t]=NaN})),o},t.reduce=function(t,n,r){if("function"!=typeof n)throw new TypeError("reducer is not a function");const e=t[Symbol.iterator]();let o,f,i=-1;if(arguments.length<3){if(({done:o,value:r}=e.next()),o)return;++i}for(;({done:o,value:f}=e.next()),!o;)r=n(r,f,++i,t);return r},t.reverse=function(t){if("function"!=typeof t[Symbol.iterator])throw new TypeError("values is not iterable");return Array.from(t).reverse()},t.rollup=q,t.rollups=R,t.scan=function(t,n){const r=lt(t,n);return r<0?void 0:r},t.shuffle=ct,t.shuffler=st,t.some=function(t,n){if("function"!=typeof n)throw new TypeError("test is not a function");let r=-1;for(const e of t)if(n(e,++r,t))return!0;return!1},t.sort=P,t.subset=function(t,n){return pt(n,t)},t.sum=function(t,n){let r=0;if(void 0===n)for(let n of t)(n=+n)&&(r+=n);else{let e=-1;for(let o of t)(o=+n(o,++e,t))&&(r+=o)}return r},t.superset=pt,t.thresholdFreedmanDiaconis=function(t,n,r){const e=g(t),o=ft(t,.75)-ft(t,.25);return e&&o?Math.ceil((r-n)/(2*o*Math.pow(e,-1/3))):1},t.thresholdScott=function(t,n,r){const e=g(t),o=A(t);return e&&o?Math.ceil((r-n)*Math.cbrt(e)/(3.49*o)):1},t.thresholdSturges=X,t.tickIncrement=V,t.tickStep=function(t,n,r){r=+r;const e=(n=+n)<(t=+t),o=e?V(n,t,r):V(t,n,r);return(e?-1:1)*(o<0?1/-o:o)},t.ticks=Q,t.transpose=at,t.union=function(...t){const n=new InternSet;for(const r of t)for(const t of r)n.add(t);return n},t.variance=b,t.zip=function(){return at(arguments)}}));

// https://d3js.org/d3-geo/ v3.1.1 Copyright 2010-2024 Mike Bostock, 2008-2012 Charles Karney
!function(n,t){"object"==typeof exports&&"undefined"!=typeof module?t(exports,require("d3-array")):"function"==typeof define&&define.amd?define(["exports","d3-array"],t):t((n="undefined"!=typeof globalThis?globalThis:n||self).d3=n.d3||{},n.d3)}(this,(function(n,t){"use strict";var r=1e-6,e=1e-12,i=Math.PI,o=i/2,u=i/4,a=2*i,c=180/i,l=i/180,f=Math.abs,p=Math.atan,s=Math.atan2,h=Math.cos,g=Math.ceil,d=Math.exp,v=Math.hypot,E=Math.log,y=Math.pow,S=Math.sin,m=Math.sign||function(n){return n>0?1:n<0?-1:0},M=Math.sqrt,w=Math.tan;function x(n){return n>1?0:n<-1?i:Math.acos(n)}function _(n){return n>1?o:n<-1?-o:Math.asin(n)}function N(n){return(n=S(n/2))*n}function A(){}function R(n,t){n&&P.hasOwnProperty(n.type)&&P[n.type](n,t)}var C={Feature:function(n,t){R(n.geometry,t)},FeatureCollection:function(n,t){for(var r=n.features,e=-1,i=r.length;++e<i;)R(r[e].geometry,t)}},P={Sphere:function(n,t){t.sphere()},Point:function(n,t){n=n.coordinates,t.point(n[0],n[1],n[2])},MultiPoint:function(n,t){for(var r=n.coordinates,e=-1,i=r.length;++e<i;)n=r[e],t.point(n[0],n[1],n[2])},LineString:function(n,t){$(n.coordinates,t,0)},MultiLineString:function(n,t){for(var r=n.coordinates,e=-1,i=r.length;++e<i;)$(r[e],t,0)},Polygon:function(n,t){q(n.coordinates,t)},MultiPolygon:function(n,t){for(var r=n.coordinates,e=-1,i=r.length;++e<i;)q(r[e],t)},GeometryCollection:function(n,t){for(var r=n.geometries,e=-1,i=r.length;++e<i;)R(r[e],t)}};function $(n,t,r){var e,i=-1,o=n.length-r;for(t.lineStart();++i<o;)e=n[i],t.point(e[0],e[1],e[2]);t.lineEnd()}function q(n,t){var r=-1,e=n.length;for(t.polygonStart();++r<e;)$(n[r],t,1);t.polygonEnd()}function j(n,t){n&&C.hasOwnProperty(n.type)?C[n.type](n,t):R(n,t)}var z,b,L,T,G,O,k,F,H,I,W,X,Y,B,D,U,Z=new t.Adder,J=new t.Adder,K={point:A,lineStart:A,lineEnd:A,polygonStart:function(){Z=new t.Adder,K.lineStart=Q,K.lineEnd=V},polygonEnd:function(){var n=+Z;J.add(n<0?a+n:n),this.lineStart=this.lineEnd=this.point=A},sphere:function(){J.add(a)}};function Q(){K.point=nn}function V(){tn(z,b)}function nn(n,t){K.point=tn,z=n,b=t,L=n*=l,T=h(t=(t*=l)/2+u),G=S(t)}function tn(n,t){var r=(n*=l)-L,e=r>=0?1:-1,i=e*r,o=h(t=(t*=l)/2+u),a=S(t),c=G*a,f=T*o+c*h(i),p=c*e*S(i);Z.add(s(p,f)),L=n,T=o,G=a}function rn(n){return[s(n[1],n[0]),_(n[2])]}function en(n){var t=n[0],r=n[1],e=h(r);return[e*h(t),e*S(t),S(r)]}function on(n,t){return n[0]*t[0]+n[1]*t[1]+n[2]*t[2]}function un(n,t){return[n[1]*t[2]-n[2]*t[1],n[2]*t[0]-n[0]*t[2],n[0]*t[1]-n[1]*t[0]]}function an(n,t){n[0]+=t[0],n[1]+=t[1],n[2]+=t[2]}function cn(n,t){return[n[0]*t,n[1]*t,n[2]*t]}function ln(n){var t=M(n[0]*n[0]+n[1]*n[1]+n[2]*n[2]);n[0]/=t,n[1]/=t,n[2]/=t}var fn,pn,sn,hn,gn,dn,vn,En,yn,Sn,mn,Mn,wn,xn,_n,Nn,An={point:Rn,lineStart:Pn,lineEnd:$n,polygonStart:function(){An.point=qn,An.lineStart=jn,An.lineEnd=zn,B=new t.Adder,K.polygonStart()},polygonEnd:function(){K.polygonEnd(),An.point=Rn,An.lineStart=Pn,An.lineEnd=$n,Z<0?(O=-(F=180),k=-(H=90)):B>r?H=90:B<-r&&(k=-90),U[0]=O,U[1]=F},sphere:function(){O=-(F=180),k=-(H=90)}};function Rn(n,t){D.push(U=[O=n,F=n]),t<k&&(k=t),t>H&&(H=t)}function Cn(n,t){var r=en([n*l,t*l]);if(Y){var e=un(Y,r),i=un([e[1],-e[0],0],e);ln(i),i=rn(i);var o,u=n-I,a=u>0?1:-1,p=i[0]*c*a,s=f(u)>180;s^(a*I<p&&p<a*n)?(o=i[1]*c)>H&&(H=o):s^(a*I<(p=(p+360)%360-180)&&p<a*n)?(o=-i[1]*c)<k&&(k=o):(t<k&&(k=t),t>H&&(H=t)),s?n<I?bn(O,n)>bn(O,F)&&(F=n):bn(n,F)>bn(O,F)&&(O=n):F>=O?(n<O&&(O=n),n>F&&(F=n)):n>I?bn(O,n)>bn(O,F)&&(F=n):bn(n,F)>bn(O,F)&&(O=n)}else D.push(U=[O=n,F=n]);t<k&&(k=t),t>H&&(H=t),Y=r,I=n}function Pn(){An.point=Cn}function $n(){U[0]=O,U[1]=F,An.point=Rn,Y=null}function qn(n,t){if(Y){var r=n-I;B.add(f(r)>180?r+(r>0?360:-360):r)}else W=n,X=t;K.point(n,t),Cn(n,t)}function jn(){K.lineStart()}function zn(){qn(W,X),K.lineEnd(),f(B)>r&&(O=-(F=180)),U[0]=O,U[1]=F,Y=null}function bn(n,t){return(t-=n)<0?t+360:t}function Ln(n,t){return n[0]-t[0]}function Tn(n,t){return n[0]<=n[1]?n[0]<=t&&t<=n[1]:t<n[0]||n[1]<t}var Gn={sphere:A,point:On,lineStart:Fn,lineEnd:Wn,polygonStart:function(){Gn.lineStart=Xn,Gn.lineEnd=Yn},polygonEnd:function(){Gn.lineStart=Fn,Gn.lineEnd=Wn}};function On(n,t){n*=l;var r=h(t*=l);kn(r*h(n),r*S(n),S(t))}function kn(n,t,r){++fn,sn+=(n-sn)/fn,hn+=(t-hn)/fn,gn+=(r-gn)/fn}function Fn(){Gn.point=Hn}function Hn(n,t){n*=l;var r=h(t*=l);xn=r*h(n),_n=r*S(n),Nn=S(t),Gn.point=In,kn(xn,_n,Nn)}function In(n,t){n*=l;var r=h(t*=l),e=r*h(n),i=r*S(n),o=S(t),u=s(M((u=_n*o-Nn*i)*u+(u=Nn*e-xn*o)*u+(u=xn*i-_n*e)*u),xn*e+_n*i+Nn*o);pn+=u,dn+=u*(xn+(xn=e)),vn+=u*(_n+(_n=i)),En+=u*(Nn+(Nn=o)),kn(xn,_n,Nn)}function Wn(){Gn.point=On}function Xn(){Gn.point=Bn}function Yn(){Dn(Mn,wn),Gn.point=On}function Bn(n,t){Mn=n,wn=t,n*=l,t*=l,Gn.point=Dn;var r=h(t);xn=r*h(n),_n=r*S(n),Nn=S(t),kn(xn,_n,Nn)}function Dn(n,t){n*=l;var r=h(t*=l),e=r*h(n),i=r*S(n),o=S(t),u=_n*o-Nn*i,a=Nn*e-xn*o,c=xn*i-_n*e,f=v(u,a,c),p=_(f),s=f&&-p/f;yn.add(s*u),Sn.add(s*a),mn.add(s*c),pn+=p,dn+=p*(xn+(xn=e)),vn+=p*(_n+(_n=i)),En+=p*(Nn+(Nn=o)),kn(xn,_n,Nn)}function Un(n){return function(){return n}}function Zn(n,t){function r(r,e){return r=n(r,e),t(r[0],r[1])}return n.invert&&t.invert&&(r.invert=function(r,e){return(r=t.invert(r,e))&&n.invert(r[0],r[1])}),r}function Jn(n,t){return f(n)>i&&(n-=Math.round(n/a)*a),[n,t]}function Kn(n,t,r){return(n%=a)?t||r?Zn(Vn(n),nt(t,r)):Vn(n):t||r?nt(t,r):Jn}function Qn(n){return function(t,r){return f(t+=n)>i&&(t-=Math.round(t/a)*a),[t,r]}}function Vn(n){var t=Qn(n);return t.invert=Qn(-n),t}function nt(n,t){var r=h(n),e=S(n),i=h(t),o=S(t);function u(n,t){var u=h(t),a=h(n)*u,c=S(n)*u,l=S(t),f=l*r+a*e;return[s(c*i-f*o,a*r-l*e),_(f*i+c*o)]}return u.invert=function(n,t){var u=h(t),a=h(n)*u,c=S(n)*u,l=S(t),f=l*i-c*o;return[s(c*i+l*o,a*r+f*e),_(f*r-a*e)]},u}function tt(n){function t(t){return(t=n(t[0]*l,t[1]*l))[0]*=c,t[1]*=c,t}return n=Kn(n[0]*l,n[1]*l,n.length>2?n[2]*l:0),t.invert=function(t){return(t=n.invert(t[0]*l,t[1]*l))[0]*=c,t[1]*=c,t},t}function rt(n,t,r,e,i,o){if(r){var u=h(t),c=S(t),l=e*r;null==i?(i=t+e*a,o=t-l/2):(i=et(u,i),o=et(u,o),(e>0?i<o:i>o)&&(i+=e*a));for(var f,p=i;e>0?p>o:p<o;p-=l)f=rn([u,-c*h(p),-c*S(p)]),n.point(f[0],f[1])}}function et(n,t){(t=en(t))[0]-=n,ln(t);var e=x(-t[1]);return((-t[2]<0?-e:e)+a-r)%a}function it(){var n,t=[];return{point:function(t,r,e){n.push([t,r,e])},lineStart:function(){t.push(n=[])},lineEnd:A,rejoin:function(){t.length>1&&t.push(t.pop().concat(t.shift()))},result:function(){var r=t;return t=[],n=null,r}}}function ot(n,t){return f(n[0]-t[0])<r&&f(n[1]-t[1])<r}function ut(n,t,r,e){this.x=n,this.z=t,this.o=r,this.e=e,this.v=!1,this.n=this.p=null}function at(n,t,e,i,o){var u,a,c=[],l=[];if(n.forEach((function(n){if(!((t=n.length-1)<=0)){var t,e,i=n[0],a=n[t];if(ot(i,a)){if(!i[2]&&!a[2]){for(o.lineStart(),u=0;u<t;++u)o.point((i=n[u])[0],i[1]);return void o.lineEnd()}a[0]+=2*r}c.push(e=new ut(i,n,null,!0)),l.push(e.o=new ut(i,null,e,!1)),c.push(e=new ut(a,n,null,!1)),l.push(e.o=new ut(a,null,e,!0))}})),c.length){for(l.sort(t),ct(c),ct(l),u=0,a=l.length;u<a;++u)l[u].e=e=!e;for(var f,p,s=c[0];;){for(var h=s,g=!0;h.v;)if((h=h.n)===s)return;f=h.z,o.lineStart();do{if(h.v=h.o.v=!0,h.e){if(g)for(u=0,a=f.length;u<a;++u)o.point((p=f[u])[0],p[1]);else i(h.x,h.n.x,1,o);h=h.n}else{if(g)for(f=h.p.z,u=f.length-1;u>=0;--u)o.point((p=f[u])[0],p[1]);else i(h.x,h.p.x,-1,o);h=h.p}f=(h=h.o).z,g=!g}while(!h.v);o.lineEnd()}}}function ct(n){if(t=n.length){for(var t,r,e=0,i=n[0];++e<t;)i.n=r=n[e],r.p=i,i=r;i.n=r=n[0],r.p=i}}function lt(n){return f(n[0])<=i?n[0]:m(n[0])*((f(n[0])+i)%a-i)}function ft(n,c){var l=lt(c),f=c[1],p=S(f),g=[S(l),-h(l),0],d=0,v=0,E=new t.Adder;1===p?f=o+r:-1===p&&(f=-o-r);for(var y=0,m=n.length;y<m;++y)if(w=(M=n[y]).length)for(var M,w,x=M[w-1],N=lt(x),A=x[1]/2+u,R=S(A),C=h(A),P=0;P<w;++P,N=q,R=z,C=b,x=$){var $=M[P],q=lt($),j=$[1]/2+u,z=S(j),b=h(j),L=q-N,T=L>=0?1:-1,G=T*L,O=G>i,k=R*z;if(E.add(s(k*T*S(G),C*b+k*h(G))),d+=O?L+T*a:L,O^N>=l^q>=l){var F=un(en(x),en($));ln(F);var H=un(g,F);ln(H);var I=(O^L>=0?-1:1)*_(H[2]);(f>I||f===I&&(F[0]||F[1]))&&(v+=O^L>=0?1:-1)}}return(d<-r||d<r&&E<-e)^1&v}function pt(n,r,e,i){return function(o){var u,a,c,l=r(o),f=it(),p=r(f),s=!1,h={point:g,lineStart:v,lineEnd:E,polygonStart:function(){h.point=y,h.lineStart=S,h.lineEnd=m,a=[],u=[]},polygonEnd:function(){h.point=g,h.lineStart=v,h.lineEnd=E,a=t.merge(a);var n=ft(u,i);a.length?(s||(o.polygonStart(),s=!0),at(a,ht,n,e,o)):n&&(s||(o.polygonStart(),s=!0),o.lineStart(),e(null,null,1,o),o.lineEnd()),s&&(o.polygonEnd(),s=!1),a=u=null},sphere:function(){o.polygonStart(),o.lineStart(),e(null,null,1,o),o.lineEnd(),o.polygonEnd()}};function g(t,r){n(t,r)&&o.point(t,r)}function d(n,t){l.point(n,t)}function v(){h.point=d,l.lineStart()}function E(){h.point=g,l.lineEnd()}function y(n,t){c.push([n,t]),p.point(n,t)}function S(){p.lineStart(),c=[]}function m(){y(c[0][0],c[0][1]),p.lineEnd();var n,t,r,e,i=p.clean(),l=f.result(),h=l.length;if(c.pop(),u.push(c),c=null,h)if(1&i){if((t=(r=l[0]).length-1)>0){for(s||(o.polygonStart(),s=!0),o.lineStart(),n=0;n<t;++n)o.point((e=r[n])[0],e[1]);o.lineEnd()}}else h>1&&2&i&&l.push(l.pop().concat(l.shift())),a.push(l.filter(st))}return h}}function st(n){return n.length>1}function ht(n,t){return((n=n.x)[0]<0?n[1]-o-r:o-n[1])-((t=t.x)[0]<0?t[1]-o-r:o-t[1])}Jn.invert=Jn;var gt=pt((function(){return!0}),(function(n){var t,e=NaN,u=NaN,a=NaN;return{lineStart:function(){n.lineStart(),t=1},point:function(c,l){var s=c>0?i:-i,g=f(c-e);f(g-i)<r?(n.point(e,u=(u+l)/2>0?o:-o),n.point(a,u),n.lineEnd(),n.lineStart(),n.point(s,u),n.point(c,u),t=0):a!==s&&g>=i&&(f(e-a)<r&&(e-=a*r),f(c-s)<r&&(c-=s*r),u=function(n,t,e,i){var o,u,a=S(n-e);return f(a)>r?p((S(t)*(u=h(i))*S(e)-S(i)*(o=h(t))*S(n))/(o*u*a)):(t+i)/2}(e,u,c,l),n.point(a,u),n.lineEnd(),n.lineStart(),n.point(s,u),t=0),n.point(e=c,u=l),a=s},lineEnd:function(){n.lineEnd(),e=u=NaN},clean:function(){return 2-t}}}),(function(n,t,e,u){var a;if(null==n)a=e*o,u.point(-i,a),u.point(0,a),u.point(i,a),u.point(i,0),u.point(i,-a),u.point(0,-a),u.point(-i,-a),u.point(-i,0),u.point(-i,a);else if(f(n[0]-t[0])>r){var c=n[0]<t[0]?i:-i;a=e*c/2,u.point(-c,a),u.point(0,a),u.point(c,a)}else u.point(t[0],t[1])}),[-i,-o]);function dt(n){var t=h(n),e=2*l,o=t>0,u=f(t)>r;function a(n,r){return h(n)*h(r)>t}function c(n,e,o){var u=[1,0,0],a=un(en(n),en(e)),c=on(a,a),l=a[0],p=c-l*l;if(!p)return!o&&n;var s=t*c/p,h=-t*l/p,g=un(u,a),d=cn(u,s);an(d,cn(a,h));var v=g,E=on(d,v),y=on(v,v),S=E*E-y*(on(d,d)-1);if(!(S<0)){var m=M(S),w=cn(v,(-E-m)/y);if(an(w,d),w=rn(w),!o)return w;var x,_=n[0],N=e[0],A=n[1],R=e[1];N<_&&(x=_,_=N,N=x);var C=N-_,P=f(C-i)<r;if(!P&&R<A&&(x=A,A=R,R=x),P||C<r?P?A+R>0^w[1]<(f(w[0]-_)<r?A:R):A<=w[1]&&w[1]<=R:C>i^(_<=w[0]&&w[0]<=N)){var $=cn(v,(-E+m)/y);return an($,d),[w,rn($)]}}}function p(t,r){var e=o?n:i-n,u=0;return t<-e?u|=1:t>e&&(u|=2),r<-e?u|=4:r>e&&(u|=8),u}return pt(a,(function(n){var t,r,e,l,f;return{lineStart:function(){l=e=!1,f=1},point:function(s,h){var g,d=[s,h],v=a(s,h),E=o?v?0:p(s,h):v?p(s+(s<0?i:-i),h):0;if(!t&&(l=e=v)&&n.lineStart(),v!==e&&(!(g=c(t,d))||ot(t,g)||ot(d,g))&&(d[2]=1),v!==e)f=0,v?(n.lineStart(),g=c(d,t),n.point(g[0],g[1])):(g=c(t,d),n.point(g[0],g[1],2),n.lineEnd()),t=g;else if(u&&t&&o^v){var y;E&r||!(y=c(d,t,!0))||(f=0,o?(n.lineStart(),n.point(y[0][0],y[0][1]),n.point(y[1][0],y[1][1]),n.lineEnd()):(n.point(y[1][0],y[1][1]),n.lineEnd(),n.lineStart(),n.point(y[0][0],y[0][1],3)))}!v||t&&ot(t,d)||n.point(d[0],d[1]),t=d,e=v,r=E},lineEnd:function(){e&&n.lineEnd(),t=null},clean:function(){return f|(l&&e)<<1}}}),(function(t,r,i,o){rt(o,n,e,i,t,r)}),o?[0,-n]:[-i,n-i])}var vt,Et,yt,St,mt=1e9,Mt=-mt;function wt(n,e,i,o){function u(t,r){return n<=t&&t<=i&&e<=r&&r<=o}function a(t,r,u,a){var l=0,f=0;if(null==t||(l=c(t,u))!==(f=c(r,u))||p(t,r)<0^u>0)do{a.point(0===l||3===l?n:i,l>1?o:e)}while((l=(l+u+4)%4)!==f);else a.point(r[0],r[1])}function c(t,o){return f(t[0]-n)<r?o>0?0:3:f(t[0]-i)<r?o>0?2:1:f(t[1]-e)<r?o>0?1:0:o>0?3:2}function l(n,t){return p(n.x,t.x)}function p(n,t){var r=c(n,1),e=c(t,1);return r!==e?r-e:0===r?t[1]-n[1]:1===r?n[0]-t[0]:2===r?n[1]-t[1]:t[0]-n[0]}return function(r){var c,f,p,s,h,g,d,v,E,y,S,m=r,M=it(),w={point:x,lineStart:function(){w.point=_,f&&f.push(p=[]);y=!0,E=!1,d=v=NaN},lineEnd:function(){c&&(_(s,h),g&&E&&M.rejoin(),c.push(M.result()));w.point=x,E&&m.lineEnd()},polygonStart:function(){m=M,c=[],f=[],S=!0},polygonEnd:function(){var e=function(){for(var t=0,r=0,e=f.length;r<e;++r)for(var i,u,a=f[r],c=1,l=a.length,p=a[0],s=p[0],h=p[1];c<l;++c)i=s,u=h,s=(p=a[c])[0],h=p[1],u<=o?h>o&&(s-i)*(o-u)>(h-u)*(n-i)&&++t:h<=o&&(s-i)*(o-u)<(h-u)*(n-i)&&--t;return t}(),i=S&&e,u=(c=t.merge(c)).length;(i||u)&&(r.polygonStart(),i&&(r.lineStart(),a(null,null,1,r),r.lineEnd()),u&&at(c,l,e,a,r),r.polygonEnd());m=r,c=f=p=null}};function x(n,t){u(n,t)&&m.point(n,t)}function _(t,r){var a=u(t,r);if(f&&p.push([t,r]),y)s=t,h=r,g=a,y=!1,a&&(m.lineStart(),m.point(t,r));else if(a&&E)m.point(t,r);else{var c=[d=Math.max(Mt,Math.min(mt,d)),v=Math.max(Mt,Math.min(mt,v))],l=[t=Math.max(Mt,Math.min(mt,t)),r=Math.max(Mt,Math.min(mt,r))];!function(n,t,r,e,i,o){var u,a=n[0],c=n[1],l=0,f=1,p=t[0]-a,s=t[1]-c;if(u=r-a,p||!(u>0)){if(u/=p,p<0){if(u<l)return;u<f&&(f=u)}else if(p>0){if(u>f)return;u>l&&(l=u)}if(u=i-a,p||!(u<0)){if(u/=p,p<0){if(u>f)return;u>l&&(l=u)}else if(p>0){if(u<l)return;u<f&&(f=u)}if(u=e-c,s||!(u>0)){if(u/=s,s<0){if(u<l)return;u<f&&(f=u)}else if(s>0){if(u>f)return;u>l&&(l=u)}if(u=o-c,s||!(u<0)){if(u/=s,s<0){if(u>f)return;u>l&&(l=u)}else if(s>0){if(u<l)return;u<f&&(f=u)}return l>0&&(n[0]=a+l*p,n[1]=c+l*s),f<1&&(t[0]=a+f*p,t[1]=c+f*s),!0}}}}}(c,l,n,e,i,o)?a&&(m.lineStart(),m.point(t,r),S=!1):(E||(m.lineStart(),m.point(c[0],c[1])),m.point(l[0],l[1]),a||m.lineEnd(),S=!1)}d=t,v=r,E=a}return w}}var xt={sphere:A,point:A,lineStart:function(){xt.point=Nt,xt.lineEnd=_t},lineEnd:A,polygonStart:A,polygonEnd:A};function _t(){xt.point=xt.lineEnd=A}function Nt(n,t){Et=n*=l,yt=S(t*=l),St=h(t),xt.point=At}function At(n,t){n*=l;var r=S(t*=l),e=h(t),i=f(n-Et),o=h(i),u=e*S(i),a=St*r-yt*e*o,c=yt*r+St*e*o;vt.add(s(M(u*u+a*a),c)),Et=n,yt=r,St=e}function Rt(n){return vt=new t.Adder,j(n,xt),+vt}var Ct=[null,null],Pt={type:"LineString",coordinates:Ct};function $t(n,t){return Ct[0]=n,Ct[1]=t,Rt(Pt)}var qt={Feature:function(n,t){return zt(n.geometry,t)},FeatureCollection:function(n,t){for(var r=n.features,e=-1,i=r.length;++e<i;)if(zt(r[e].geometry,t))return!0;return!1}},jt={Sphere:function(){return!0},Point:function(n,t){return bt(n.coordinates,t)},MultiPoint:function(n,t){for(var r=n.coordinates,e=-1,i=r.length;++e<i;)if(bt(r[e],t))return!0;return!1},LineString:function(n,t){return Lt(n.coordinates,t)},MultiLineString:function(n,t){for(var r=n.coordinates,e=-1,i=r.length;++e<i;)if(Lt(r[e],t))return!0;return!1},Polygon:function(n,t){return Tt(n.coordinates,t)},MultiPolygon:function(n,t){for(var r=n.coordinates,e=-1,i=r.length;++e<i;)if(Tt(r[e],t))return!0;return!1},GeometryCollection:function(n,t){for(var r=n.geometries,e=-1,i=r.length;++e<i;)if(zt(r[e],t))return!0;return!1}};function zt(n,t){return!(!n||!jt.hasOwnProperty(n.type))&&jt[n.type](n,t)}function bt(n,t){return 0===$t(n,t)}function Lt(n,t){for(var r,i,o,u=0,a=n.length;u<a;u++){if(0===(i=$t(n[u],t)))return!0;if(u>0&&(o=$t(n[u],n[u-1]))>0&&r<=o&&i<=o&&(r+i-o)*(1-Math.pow((r-i)/o,2))<e*o)return!0;r=i}return!1}function Tt(n,t){return!!ft(n.map(Gt),Ot(t))}function Gt(n){return(n=n.map(Ot)).pop(),n}function Ot(n){return[n[0]*l,n[1]*l]}function kt(n,e,i){var o=t.range(n,e-r,i).concat(e);return function(n){return o.map((function(t){return[n,t]}))}}function Ft(n,e,i){var o=t.range(n,e-r,i).concat(e);return function(n){return o.map((function(t){return[t,n]}))}}function Ht(){var n,e,i,o,u,a,c,l,p,s,h,d,v=10,E=v,y=90,S=360,m=2.5;function M(){return{type:"MultiLineString",coordinates:w()}}function w(){return t.range(g(o/y)*y,i,y).map(h).concat(t.range(g(l/S)*S,c,S).map(d)).concat(t.range(g(e/v)*v,n,v).filter((function(n){return f(n%y)>r})).map(p)).concat(t.range(g(a/E)*E,u,E).filter((function(n){return f(n%S)>r})).map(s))}return M.lines=function(){return w().map((function(n){return{type:"LineString",coordinates:n}}))},M.outline=function(){return{type:"Polygon",coordinates:[h(o).concat(d(c).slice(1),h(i).reverse().slice(1),d(l).reverse().slice(1))]}},M.extent=function(n){return arguments.length?M.extentMajor(n).extentMinor(n):M.extentMinor()},M.extentMajor=function(n){return arguments.length?(o=+n[0][0],i=+n[1][0],l=+n[0][1],c=+n[1][1],o>i&&(n=o,o=i,i=n),l>c&&(n=l,l=c,c=n),M.precision(m)):[[o,l],[i,c]]},M.extentMinor=function(t){return arguments.length?(e=+t[0][0],n=+t[1][0],a=+t[0][1],u=+t[1][1],e>n&&(t=e,e=n,n=t),a>u&&(t=a,a=u,u=t),M.precision(m)):[[e,a],[n,u]]},M.step=function(n){return arguments.length?M.stepMajor(n).stepMinor(n):M.stepMinor()},M.stepMajor=function(n){return arguments.length?(y=+n[0],S=+n[1],M):[y,S]},M.stepMinor=function(n){return arguments.length?(v=+n[0],E=+n[1],M):[v,E]},M.precision=function(t){return arguments.length?(m=+t,p=kt(a,u,90),s=Ft(e,n,m),h=kt(l,c,90),d=Ft(o,i,m),M):m},M.extentMajor([[-180,-90+r],[180,90-r]]).extentMinor([[-180,-80-r],[180,80+r]])}var It,Wt,Xt,Yt,Bt=n=>n,Dt=new t.Adder,Ut=new t.Adder,Zt={point:A,lineStart:A,lineEnd:A,polygonStart:function(){Zt.lineStart=Jt,Zt.lineEnd=Vt},polygonEnd:function(){Zt.lineStart=Zt.lineEnd=Zt.point=A,Dt.add(f(Ut)),Ut=new t.Adder},result:function(){var n=Dt/2;return Dt=new t.Adder,n}};function Jt(){Zt.point=Kt}function Kt(n,t){Zt.point=Qt,It=Xt=n,Wt=Yt=t}function Qt(n,t){Ut.add(Yt*n-Xt*t),Xt=n,Yt=t}function Vt(){Qt(It,Wt)}var nr=1/0,tr=nr,rr=-nr,er=rr,ir={point:function(n,t){n<nr&&(nr=n);n>rr&&(rr=n);t<tr&&(tr=t);t>er&&(er=t)},lineStart:A,lineEnd:A,polygonStart:A,polygonEnd:A,result:function(){var n=[[nr,tr],[rr,er]];return rr=er=-(tr=nr=1/0),n}};var or,ur,ar,cr,lr=0,fr=0,pr=0,sr=0,hr=0,gr=0,dr=0,vr=0,Er=0,yr={point:Sr,lineStart:mr,lineEnd:xr,polygonStart:function(){yr.lineStart=_r,yr.lineEnd=Nr},polygonEnd:function(){yr.point=Sr,yr.lineStart=mr,yr.lineEnd=xr},result:function(){var n=Er?[dr/Er,vr/Er]:gr?[sr/gr,hr/gr]:pr?[lr/pr,fr/pr]:[NaN,NaN];return lr=fr=pr=sr=hr=gr=dr=vr=Er=0,n}};function Sr(n,t){lr+=n,fr+=t,++pr}function mr(){yr.point=Mr}function Mr(n,t){yr.point=wr,Sr(ar=n,cr=t)}function wr(n,t){var r=n-ar,e=t-cr,i=M(r*r+e*e);sr+=i*(ar+n)/2,hr+=i*(cr+t)/2,gr+=i,Sr(ar=n,cr=t)}function xr(){yr.point=Sr}function _r(){yr.point=Ar}function Nr(){Rr(or,ur)}function Ar(n,t){yr.point=Rr,Sr(or=ar=n,ur=cr=t)}function Rr(n,t){var r=n-ar,e=t-cr,i=M(r*r+e*e);sr+=i*(ar+n)/2,hr+=i*(cr+t)/2,gr+=i,dr+=(i=cr*n-ar*t)*(ar+n),vr+=i*(cr+t),Er+=3*i,Sr(ar=n,cr=t)}function Cr(n){this._context=n}Cr.prototype={_radius:4.5,pointRadius:function(n){return this._radius=n,this},polygonStart:function(){this._line=0},polygonEnd:function(){this._line=NaN},lineStart:function(){this._point=0},lineEnd:function(){0===this._line&&this._context.closePath(),this._point=NaN},point:function(n,t){switch(this._point){case 0:this._context.moveTo(n,t),this._point=1;break;case 1:this._context.lineTo(n,t);break;default:this._context.moveTo(n+this._radius,t),this._context.arc(n,t,this._radius,0,a)}},result:A};var Pr,$r,qr,jr,zr,br=new t.Adder,Lr={point:A,lineStart:function(){Lr.point=Tr},lineEnd:function(){Pr&&Gr($r,qr),Lr.point=A},polygonStart:function(){Pr=!0},polygonEnd:function(){Pr=null},result:function(){var n=+br;return br=new t.Adder,n}};function Tr(n,t){Lr.point=Gr,$r=jr=n,qr=zr=t}function Gr(n,t){jr-=n,zr-=t,br.add(M(jr*jr+zr*zr)),jr=n,zr=t}let Or,kr,Fr,Hr;class Ir{constructor(n){this._append=null==n?Wr:function(n){const t=Math.floor(n);if(!(t>=0))throw new RangeError(`invalid digits: ${n}`);if(t>15)return Wr;if(t!==Or){const n=10**t;Or=t,kr=function(t){let r=1;this._+=t[0];for(const e=t.length;r<e;++r)this._+=Math.round(arguments[r]*n)/n+t[r]}}return kr}(n),this._radius=4.5,this._=""}pointRadius(n){return this._radius=+n,this}polygonStart(){this._line=0}polygonEnd(){this._line=NaN}lineStart(){this._point=0}lineEnd(){0===this._line&&(this._+="Z"),this._point=NaN}point(n,t){switch(this._point){case 0:this._append`M${n},${t}`,this._point=1;break;case 1:this._append`L${n},${t}`;break;default:if(this._append`M${n},${t}`,this._radius!==Fr||this._append!==kr){const n=this._radius,t=this._;this._="",this._append`m0,${n}a${n},${n} 0 1,1 0,${-2*n}a${n},${n} 0 1,1 0,${2*n}z`,Fr=n,kr=this._append,Hr=this._,this._=t}this._+=Hr}}result(){const n=this._;return this._="",n.length?n:null}}function Wr(n){let t=1;this._+=n[0];for(const r=n.length;t<r;++t)this._+=arguments[t]+n[t]}function Xr(n){return function(t){var r=new Yr;for(var e in n)r[e]=n[e];return r.stream=t,r}}function Yr(){}function Br(n,t,r){var e=n.clipExtent&&n.clipExtent();return n.scale(150).translate([0,0]),null!=e&&n.clipExtent(null),j(r,n.stream(ir)),t(ir.result()),null!=e&&n.clipExtent(e),n}function Dr(n,t,r){return Br(n,(function(r){var e=t[1][0]-t[0][0],i=t[1][1]-t[0][1],o=Math.min(e/(r[1][0]-r[0][0]),i/(r[1][1]-r[0][1])),u=+t[0][0]+(e-o*(r[1][0]+r[0][0]))/2,a=+t[0][1]+(i-o*(r[1][1]+r[0][1]))/2;n.scale(150*o).translate([u,a])}),r)}function Ur(n,t,r){return Dr(n,[[0,0],t],r)}function Zr(n,t,r){return Br(n,(function(r){var e=+t,i=e/(r[1][0]-r[0][0]),o=(e-i*(r[1][0]+r[0][0]))/2,u=-i*r[0][1];n.scale(150*i).translate([o,u])}),r)}function Jr(n,t,r){return Br(n,(function(r){var e=+t,i=e/(r[1][1]-r[0][1]),o=-i*r[0][0],u=(e-i*(r[1][1]+r[0][1]))/2;n.scale(150*i).translate([o,u])}),r)}Yr.prototype={constructor:Yr,point:function(n,t){this.stream.point(n,t)},sphere:function(){this.stream.sphere()},lineStart:function(){this.stream.lineStart()},lineEnd:function(){this.stream.lineEnd()},polygonStart:function(){this.stream.polygonStart()},polygonEnd:function(){this.stream.polygonEnd()}};var Kr=16,Qr=h(30*l);function Vr(n,t){return+t?function(n,t){function e(i,o,u,a,c,l,p,h,g,d,v,E,y,S){var m=p-i,w=h-o,x=m*m+w*w;if(x>4*t&&y--){var N=a+d,A=c+v,R=l+E,C=M(N*N+A*A+R*R),P=_(R/=C),$=f(f(R)-1)<r||f(u-g)<r?(u+g)/2:s(A,N),q=n($,P),j=q[0],z=q[1],b=j-i,L=z-o,T=w*b-m*L;(T*T/x>t||f((m*b+w*L)/x-.5)>.3||a*d+c*v+l*E<Qr)&&(e(i,o,u,a,c,l,j,z,$,N/=C,A/=C,R,y,S),S.point(j,z),e(j,z,$,N,A,R,p,h,g,d,v,E,y,S))}}return function(t){var r,i,o,u,a,c,l,f,p,s,h,g,d={point:v,lineStart:E,lineEnd:S,polygonStart:function(){t.polygonStart(),d.lineStart=m},polygonEnd:function(){t.polygonEnd(),d.lineStart=E}};function v(r,e){r=n(r,e),t.point(r[0],r[1])}function E(){f=NaN,d.point=y,t.lineStart()}function y(r,i){var o=en([r,i]),u=n(r,i);e(f,p,l,s,h,g,f=u[0],p=u[1],l=r,s=o[0],h=o[1],g=o[2],Kr,t),t.point(f,p)}function S(){d.point=v,t.lineEnd()}function m(){E(),d.point=M,d.lineEnd=w}function M(n,t){y(r=n,t),i=f,o=p,u=s,a=h,c=g,d.point=y}function w(){e(f,p,l,s,h,g,i,o,r,u,a,c,Kr,t),d.lineEnd=S,S()}return d}}(n,t):function(n){return Xr({point:function(t,r){t=n(t,r),this.stream.point(t[0],t[1])}})}(n)}var ne=Xr({point:function(n,t){this.stream.point(n*l,t*l)}});function te(n,t,r,e,i,o){if(!o)return function(n,t,r,e,i){function o(o,u){return[t+n*(o*=e),r-n*(u*=i)]}return o.invert=function(o,u){return[(o-t)/n*e,(r-u)/n*i]},o}(n,t,r,e,i);var u=h(o),a=S(o),c=u*n,l=a*n,f=u/n,p=a/n,s=(a*r-u*t)/n,g=(a*t+u*r)/n;function d(n,o){return[c*(n*=e)-l*(o*=i)+t,r-l*n-c*o]}return d.invert=function(n,t){return[e*(f*n-p*t+s),i*(g-p*n-f*t)]},d}function re(n){return ee((function(){return n}))()}function ee(n){var t,r,e,i,o,u,a,f,p,s,h=150,g=480,d=250,v=0,E=0,y=0,S=0,m=0,w=0,x=1,_=1,N=null,A=gt,R=null,C=Bt,P=.5;function $(n){return f(n[0]*l,n[1]*l)}function q(n){return(n=f.invert(n[0],n[1]))&&[n[0]*c,n[1]*c]}function j(){var n=te(h,0,0,x,_,w).apply(null,t(v,E)),e=te(h,g-n[0],d-n[1],x,_,w);return r=Kn(y,S,m),a=Zn(t,e),f=Zn(r,a),u=Vr(a,P),z()}function z(){return p=s=null,$}return $.stream=function(n){return p&&s===n?p:p=ne(function(n){return Xr({point:function(t,r){var e=n(t,r);return this.stream.point(e[0],e[1])}})}(r)(A(u(C(s=n)))))},$.preclip=function(n){return arguments.length?(A=n,N=void 0,z()):A},$.postclip=function(n){return arguments.length?(C=n,R=e=i=o=null,z()):C},$.clipAngle=function(n){return arguments.length?(A=+n?dt(N=n*l):(N=null,gt),z()):N*c},$.clipExtent=function(n){return arguments.length?(C=null==n?(R=e=i=o=null,Bt):wt(R=+n[0][0],e=+n[0][1],i=+n[1][0],o=+n[1][1]),z()):null==R?null:[[R,e],[i,o]]},$.scale=function(n){return arguments.length?(h=+n,j()):h},$.translate=function(n){return arguments.length?(g=+n[0],d=+n[1],j()):[g,d]},$.center=function(n){return arguments.length?(v=n[0]%360*l,E=n[1]%360*l,j()):[v*c,E*c]},$.rotate=function(n){return arguments.length?(y=n[0]%360*l,S=n[1]%360*l,m=n.length>2?n[2]%360*l:0,j()):[y*c,S*c,m*c]},$.angle=function(n){return arguments.length?(w=n%360*l,j()):w*c},$.reflectX=function(n){return arguments.length?(x=n?-1:1,j()):x<0},$.reflectY=function(n){return arguments.length?(_=n?-1:1,j()):_<0},$.precision=function(n){return arguments.length?(u=Vr(a,P=n*n),z()):M(P)},$.fitExtent=function(n,t){return Dr($,n,t)},$.fitSize=function(n,t){return Ur($,n,t)},$.fitWidth=function(n,t){return Zr($,n,t)},$.fitHeight=function(n,t){return Jr($,n,t)},function(){return t=n.apply(this,arguments),$.invert=t.invert&&q,j()}}function ie(n){var t=0,r=i/3,e=ee(n),o=e(t,r);return o.parallels=function(n){return arguments.length?e(t=n[0]*l,r=n[1]*l):[t*c,r*c]},o}function oe(n,t){var e=S(n),o=(e+S(t))/2;if(f(o)<r)return function(n){var t=h(n);function r(n,r){return[n*t,S(r)/t]}return r.invert=function(n,r){return[n/t,_(r*t)]},r}(n);var u=1+e*(2*o-e),a=M(u)/o;function c(n,t){var r=M(u-2*o*S(t))/o;return[r*S(n*=o),a-r*h(n)]}return c.invert=function(n,t){var r=a-t,e=s(n,f(r))*m(r);return r*o<0&&(e-=i*m(n)*m(r)),[e/o,_((u-(n*n+r*r)*o*o)/(2*o))]},c}function ue(){return ie(oe).scale(155.424).center([0,33.6442])}function ae(){return ue().parallels([29.5,45.5]).scale(1070).translate([480,250]).rotate([96,0]).center([-.6,38.7])}function ce(n){return function(t,r){var e=h(t),i=h(r),o=n(e*i);return o===1/0?[2,0]:[o*i*S(t),o*S(r)]}}function le(n){return function(t,r){var e=M(t*t+r*r),i=n(e),o=S(i),u=h(i);return[s(t*o,e*u),_(e&&r*o/e)]}}var fe=ce((function(n){return M(2/(1+n))}));fe.invert=le((function(n){return 2*_(n/2)}));var pe=ce((function(n){return(n=x(n))&&n/S(n)}));function se(n,t){return[n,E(w((o+t)/2))]}function he(n){var t,r,e,o=re(n),u=o.center,a=o.scale,c=o.translate,l=o.clipExtent,f=null;function p(){var u=i*a(),c=o(tt(o.rotate()).invert([0,0]));return l(null==f?[[c[0]-u,c[1]-u],[c[0]+u,c[1]+u]]:n===se?[[Math.max(c[0]-u,f),t],[Math.min(c[0]+u,r),e]]:[[f,Math.max(c[1]-u,t)],[r,Math.min(c[1]+u,e)]])}return o.scale=function(n){return arguments.length?(a(n),p()):a()},o.translate=function(n){return arguments.length?(c(n),p()):c()},o.center=function(n){return arguments.length?(u(n),p()):u()},o.clipExtent=function(n){return arguments.length?(null==n?f=t=r=e=null:(f=+n[0][0],t=+n[0][1],r=+n[1][0],e=+n[1][1]),p()):null==f?null:[[f,t],[r,e]]},p()}function ge(n){return w((o+n)/2)}function de(n,t){var e=h(n),u=n===t?S(n):E(e/h(t))/E(ge(t)/ge(n)),a=e*y(ge(n),u)/u;if(!u)return se;function c(n,t){a>0?t<-o+r&&(t=-o+r):t>o-r&&(t=o-r);var e=a/y(ge(t),u);return[e*S(u*n),a-e*h(u*n)]}return c.invert=function(n,t){var r=a-t,e=m(u)*M(n*n+r*r),c=s(n,f(r))*m(r);return r*u<0&&(c-=i*m(n)*m(r)),[c/u,2*p(y(a/e,1/u))-o]},c}function ve(n,t){return[n,t]}function Ee(n,t){var e=h(n),o=n===t?S(n):(e-h(t))/(t-n),u=e/o+n;if(f(o)<r)return ve;function a(n,t){var r=u-t,e=o*n;return[r*S(e),u-r*h(e)]}return a.invert=function(n,t){var r=u-t,e=s(n,f(r))*m(r);return r*o<0&&(e-=i*m(n)*m(r)),[e/o,u-m(o)*M(n*n+r*r)]},a}pe.invert=le((function(n){return n})),se.invert=function(n,t){return[n,2*p(d(t))-o]},ve.invert=ve;var ye=1.340264,Se=-.081106,me=893e-6,Me=.003796,we=M(3)/2;function xe(n,t){var r=_(we*S(t)),e=r*r,i=e*e*e;return[n*h(r)/(we*(ye+3*Se*e+i*(7*me+9*Me*e))),r*(ye+Se*e+i*(me+Me*e))]}function _e(n,t){var r=h(t),e=h(n)*r;return[r*S(n)/e,S(t)/e]}function Ne(n,t){var r=t*t,e=r*r;return[n*(.8707-.131979*r+e*(e*(.003971*r-.001529*e)-.013791)),t*(1.007226+r*(.015085+e*(.028874*r-.044475-.005916*e)))]}function Ae(n,t){return[h(t)*S(n),S(t)]}function Re(n,t){var r=h(t),e=1+h(n)*r;return[r*S(n)/e,S(t)/e]}function Ce(n,t){return[E(w((o+t)/2)),-n]}xe.invert=function(n,t){for(var r,i=t,o=i*i,u=o*o*o,a=0;a<12&&(u=(o=(i-=r=(i*(ye+Se*o+u*(me+Me*o))-t)/(ye+3*Se*o+u*(7*me+9*Me*o)))*i)*o*o,!(f(r)<e));++a);return[we*n*(ye+3*Se*o+u*(7*me+9*Me*o))/h(i),_(S(i)/we)]},_e.invert=le(p),Ne.invert=function(n,t){var e,i=t,o=25;do{var u=i*i,a=u*u;i-=e=(i*(1.007226+u*(.015085+a*(.028874*u-.044475-.005916*a)))-t)/(1.007226+u*(.045255+a*(.259866*u-.311325-.005916*11*a)))}while(f(e)>r&&--o>0);return[n/(.8707+(u=i*i)*(u*(u*u*u*(.003971-.001529*u)-.013791)-.131979)),i]},Ae.invert=le(_),Re.invert=le((function(n){return 2*p(n)})),Ce.invert=function(n,t){return[-t,2*p(d(n))-o]},n.geoAlbers=ae,n.geoAlbersUsa=function(){var n,t,e,i,o,u,a=ae(),c=ue().rotate([154,0]).center([-2,58.5]).parallels([55,65]),l=ue().rotate([157,0]).center([-3,19.9]).parallels([8,18]),f={point:function(n,t){u=[n,t]}};function p(n){var t=n[0],r=n[1];return u=null,e.point(t,r),u||(i.point(t,r),u)||(o.point(t,r),u)}function s(){return n=t=null,p}return p.invert=function(n){var t=a.scale(),r=a.translate(),e=(n[0]-r[0])/t,i=(n[1]-r[1])/t;return(i>=.12&&i<.234&&e>=-.425&&e<-.214?c:i>=.166&&i<.234&&e>=-.214&&e<-.115?l:a).invert(n)},p.stream=function(r){return n&&t===r?n:(e=[a.stream(t=r),c.stream(r),l.stream(r)],i=e.length,n={point:function(n,t){for(var r=-1;++r<i;)e[r].point(n,t)},sphere:function(){for(var n=-1;++n<i;)e[n].sphere()},lineStart:function(){for(var n=-1;++n<i;)e[n].lineStart()},lineEnd:function(){for(var n=-1;++n<i;)e[n].lineEnd()},polygonStart:function(){for(var n=-1;++n<i;)e[n].polygonStart()},polygonEnd:function(){for(var n=-1;++n<i;)e[n].polygonEnd()}});var e,i},p.precision=function(n){return arguments.length?(a.precision(n),c.precision(n),l.precision(n),s()):a.precision()},p.scale=function(n){return arguments.length?(a.scale(n),c.scale(.35*n),l.scale(n),p.translate(a.translate())):a.scale()},p.translate=function(n){if(!arguments.length)return a.translate();var t=a.scale(),u=+n[0],p=+n[1];return e=a.translate(n).clipExtent([[u-.455*t,p-.238*t],[u+.455*t,p+.238*t]]).stream(f),i=c.translate([u-.307*t,p+.201*t]).clipExtent([[u-.425*t+r,p+.12*t+r],[u-.214*t-r,p+.234*t-r]]).stream(f),o=l.translate([u-.205*t,p+.212*t]).clipExtent([[u-.214*t+r,p+.166*t+r],[u-.115*t-r,p+.234*t-r]]).stream(f),s()},p.fitExtent=function(n,t){return Dr(p,n,t)},p.fitSize=function(n,t){return Ur(p,n,t)},p.fitWidth=function(n,t){return Zr(p,n,t)},p.fitHeight=function(n,t){return Jr(p,n,t)},p.scale(1070)},n.geoArea=function(n){return J=new t.Adder,j(n,K),2*J},n.geoAzimuthalEqualArea=function(){return re(fe).scale(124.75).clipAngle(179.999)},n.geoAzimuthalEqualAreaRaw=fe,n.geoAzimuthalEquidistant=function(){return re(pe).scale(79.4188).clipAngle(179.999)},n.geoAzimuthalEquidistantRaw=pe,n.geoBounds=function(n){var t,r,e,i,o,u,a;if(H=F=-(O=k=1/0),D=[],j(n,An),r=D.length){for(D.sort(Ln),t=1,o=[e=D[0]];t<r;++t)Tn(e,(i=D[t])[0])||Tn(e,i[1])?(bn(e[0],i[1])>bn(e[0],e[1])&&(e[1]=i[1]),bn(i[0],e[1])>bn(e[0],e[1])&&(e[0]=i[0])):o.push(e=i);for(u=-1/0,t=0,e=o[r=o.length-1];t<=r;e=i,++t)i=o[t],(a=bn(e[1],i[0]))>u&&(u=a,O=i[0],F=e[1])}return D=U=null,O===1/0||k===1/0?[[NaN,NaN],[NaN,NaN]]:[[O,k],[F,H]]},n.geoCentroid=function(n){fn=pn=sn=hn=gn=dn=vn=En=0,yn=new t.Adder,Sn=new t.Adder,mn=new t.Adder,j(n,Gn);var i=+yn,o=+Sn,u=+mn,a=v(i,o,u);return a<e&&(i=dn,o=vn,u=En,pn<r&&(i=sn,o=hn,u=gn),(a=v(i,o,u))<e)?[NaN,NaN]:[s(o,i)*c,_(u/a)*c]},n.geoCircle=function(){var n,t,r=Un([0,0]),e=Un(90),i=Un(2),o={point:function(r,e){n.push(r=t(r,e)),r[0]*=c,r[1]*=c}};function u(){var u=r.apply(this,arguments),a=e.apply(this,arguments)*l,c=i.apply(this,arguments)*l;return n=[],t=Kn(-u[0]*l,-u[1]*l,0).invert,rt(o,a,c,1),u={type:"Polygon",coordinates:[n]},n=t=null,u}return u.center=function(n){return arguments.length?(r="function"==typeof n?n:Un([+n[0],+n[1]]),u):r},u.radius=function(n){return arguments.length?(e="function"==typeof n?n:Un(+n),u):e},u.precision=function(n){return arguments.length?(i="function"==typeof n?n:Un(+n),u):i},u},n.geoClipAntimeridian=gt,n.geoClipCircle=dt,n.geoClipExtent=function(){var n,t,r,e=0,i=0,o=960,u=500;return r={stream:function(r){return n&&t===r?n:n=wt(e,i,o,u)(t=r)},extent:function(a){return arguments.length?(e=+a[0][0],i=+a[0][1],o=+a[1][0],u=+a[1][1],n=t=null,r):[[e,i],[o,u]]}}},n.geoClipRectangle=wt,n.geoConicConformal=function(){return ie(de).scale(109.5).parallels([30,30])},n.geoConicConformalRaw=de,n.geoConicEqualArea=ue,n.geoConicEqualAreaRaw=oe,n.geoConicEquidistant=function(){return ie(Ee).scale(131.154).center([0,13.9389])},n.geoConicEquidistantRaw=Ee,n.geoContains=function(n,t){return(n&&qt.hasOwnProperty(n.type)?qt[n.type]:zt)(n,t)},n.geoDistance=$t,n.geoEqualEarth=function(){return re(xe).scale(177.158)},n.geoEqualEarthRaw=xe,n.geoEquirectangular=function(){return re(ve).scale(152.63)},n.geoEquirectangularRaw=ve,n.geoGnomonic=function(){return re(_e).scale(144.049).clipAngle(60)},n.geoGnomonicRaw=_e,n.geoGraticule=Ht,n.geoGraticule10=function(){return Ht()()},n.geoIdentity=function(){var n,t,r,e,i,o,u,a=1,f=0,p=0,s=1,g=1,d=0,v=null,E=1,y=1,m=Xr({point:function(n,t){var r=x([n,t]);this.stream.point(r[0],r[1])}}),M=Bt;function w(){return E=a*s,y=a*g,o=u=null,x}function x(r){var e=r[0]*E,i=r[1]*y;if(d){var o=i*n-e*t;e=e*n+i*t,i=o}return[e+f,i+p]}return x.invert=function(r){var e=r[0]-f,i=r[1]-p;if(d){var o=i*n+e*t;e=e*n-i*t,i=o}return[e/E,i/y]},x.stream=function(n){return o&&u===n?o:o=m(M(u=n))},x.postclip=function(n){return arguments.length?(M=n,v=r=e=i=null,w()):M},x.clipExtent=function(n){return arguments.length?(M=null==n?(v=r=e=i=null,Bt):wt(v=+n[0][0],r=+n[0][1],e=+n[1][0],i=+n[1][1]),w()):null==v?null:[[v,r],[e,i]]},x.scale=function(n){return arguments.length?(a=+n,w()):a},x.translate=function(n){return arguments.length?(f=+n[0],p=+n[1],w()):[f,p]},x.angle=function(r){return arguments.length?(t=S(d=r%360*l),n=h(d),w()):d*c},x.reflectX=function(n){return arguments.length?(s=n?-1:1,w()):s<0},x.reflectY=function(n){return arguments.length?(g=n?-1:1,w()):g<0},x.fitExtent=function(n,t){return Dr(x,n,t)},x.fitSize=function(n,t){return Ur(x,n,t)},x.fitWidth=function(n,t){return Zr(x,n,t)},x.fitHeight=function(n,t){return Jr(x,n,t)},x},n.geoInterpolate=function(n,t){var r=n[0]*l,e=n[1]*l,i=t[0]*l,o=t[1]*l,u=h(e),a=S(e),f=h(o),p=S(o),g=u*h(r),d=u*S(r),v=f*h(i),E=f*S(i),y=2*_(M(N(o-e)+u*f*N(i-r))),m=S(y),w=y?function(n){var t=S(n*=y)/m,r=S(y-n)/m,e=r*g+t*v,i=r*d+t*E,o=r*a+t*p;return[s(i,e)*c,s(o,M(e*e+i*i))*c]}:function(){return[r*c,e*c]};return w.distance=y,w},n.geoLength=Rt,n.geoMercator=function(){return he(se).scale(961/a)},n.geoMercatorRaw=se,n.geoNaturalEarth1=function(){return re(Ne).scale(175.295)},n.geoNaturalEarth1Raw=Ne,n.geoOrthographic=function(){return re(Ae).scale(249.5).clipAngle(90+r)},n.geoOrthographicRaw=Ae,n.geoPath=function(n,t){let r,e,i=3,o=4.5;function u(n){return n&&("function"==typeof o&&e.pointRadius(+o.apply(this,arguments)),j(n,r(e))),e.result()}return u.area=function(n){return j(n,r(Zt)),Zt.result()},u.measure=function(n){return j(n,r(Lr)),Lr.result()},u.bounds=function(n){return j(n,r(ir)),ir.result()},u.centroid=function(n){return j(n,r(yr)),yr.result()},u.projection=function(t){return arguments.length?(r=null==t?(n=null,Bt):(n=t).stream,u):n},u.context=function(n){return arguments.length?(e=null==n?(t=null,new Ir(i)):new Cr(t=n),"function"!=typeof o&&e.pointRadius(o),u):t},u.pointRadius=function(n){return arguments.length?(o="function"==typeof n?n:(e.pointRadius(+n),+n),u):o},u.digits=function(n){if(!arguments.length)return i;if(null==n)i=null;else{const t=Math.floor(n);if(!(t>=0))throw new RangeError(`invalid digits: ${n}`);i=t}return null===t&&(e=new Ir(i)),u},u.projection(n).digits(i).context(t)},n.geoProjection=re,n.geoProjectionMutator=ee,n.geoRotation=tt,n.geoStereographic=function(){return re(Re).scale(250).clipAngle(142)},n.geoStereographicRaw=Re,n.geoStream=j,n.geoTransform=function(n){return{stream:Xr(n)}},n.geoTransverseMercator=function(){var n=he(Ce),t=n.center,r=n.rotate;return n.center=function(n){return arguments.length?t([-n[1],n[0]]):[(n=t())[1],-n[0]]},n.rotate=function(n){return arguments.length?r([n[0],n[1],n.length>2?n[2]+90:90]):[(n=r())[0],n[1],n[2]-90]},r([0,0,90]).scale(159.155)},n.geoTransverseMercatorRaw=Ce}));

;

(() => {
  const cards = [...document.querySelectorAll('.cards > .card')];
  const scenes = [...document.querySelectorAll('.scene')];
  const chapterEl = document.querySelector('.chapter'), chYear = chapterEl.querySelector('.ch-year'), chSub = chapterEl.querySelector('.ch-sub');
  const hint = document.querySelector('.hint');
  const articleEl = document.querySelector('.article'), stageEl = document.querySelector('.stage');
  const CHS = [["2750 AC", "El nacimiento del té"], ["600 DC", "La expansión en Oriente"], ["1368 DC", "La oscuridad emerge"], ["1657 DC", "Rumbo a Inglaterra"], ["1800 DC", "La elegancia servida"], ["1908 DC", "El accidente perfecto"]], CARD_CH = [0, 0, 1, 2, 2, 3, 4, 4, 5];
  let curCh = 0, sceneFade = [];
  const ZOOMS = [[905, 790, 3.0], [372, 700, 1.0], [1235, 735, 1.0], [595, 640, 1.0], [1200, 600, 1.0], [880, 400, 1.0], [1090, 800, 1.0], [1022, 728, 1.0], [570, 612, 2.8], [806, 728, 3.4]], arts = scenes.map(s => s.querySelector('.art'));
  const reduce = matchMedia('(prefers-reduced-motion: reduce)').matches;
  arts.forEach(a => a.style.transformOrigin = '0 0');
  const GD = {"T": {"2": {"route": "asia", "cam": [[104, 34, 3.0], [112, 33, 1.7], [118, 35, 2.6]], "hl0": ["china"], "hl1": ["china", "korea", "japan"], "labels": ["china", "japon", "corea", "tibet", "vietnam", "mongolia"], "origin": "china", "dest": "japon"}, "5": {"route": "toengland", "cam": [[104, 34, 3.0], [50, 25, 0.82], [-2, 53, 4.0]], "hl0": ["china"], "hl1": ["gb"], "labels": ["china", "india", "inglaterra"], "origin": "china", "dest": "inglaterra"}, "8": {"route": "tony", "cam": [[-2, 53, 4.0], [-40, 45, 1.25], [-90, 39, 2.6]], "hl0": ["gb"], "hl1": ["usa"], "labels": ["inglaterra", "nuevayork"], "origin": "inglaterra", "dest": "nuevayork"}}, "land": {"type": "FeatureCollection", "features": [{"type": "Feature", "id": "namerica", "geometry": {"type": "Polygon", "coordinates": [[[-168, 66], [-162, 70], [-156, 71.3], [-141, 69.6], [-128, 70], [-115, 68.5], [-95, 72], [-82, 69], [-80, 63], [-94, 59], [-92, 57], [-82, 55], [-79, 52], [-77, 60], [-70, 62], [-64, 60], [-61, 56], [-56, 52], [-59, 48], [-65, 48], [-64, 45], [-70, 43.5], [-70, 41.6], [-74, 40.5], [-76, 37], [-75.5, 35], [-81, 31.5], [-80, 27], [-80.5, 25.2], [-82, 26.5], [-83, 29.8], [-89, 30.2], [-94, 29.6], [-97, 27.8], [-97.5, 22], [-95, 18.5], [-91, 18.8], [-90.5, 21], [-87, 21.5], [-88, 16], [-84, 15], [-83.5, 11], [-80, 8.5], [-77.5, 8.5], [-79.5, 7], [-83, 8.5], [-86, 12], [-91.5, 14], [-96, 15.8], [-105, 19.5], [-105.5, 23], [-109.5, 23], [-112, 27], [-114.7, 31.7], [-114, 30], [-110, 23], [-112, 25], [-115, 29.5], [-117, 32.5], [-118.5, 34], [-121, 35], [-122.5, 37.5], [-124, 40.5], [-124, 46], [-124.5, 48.5], [-127, 50.5], [-131, 54], [-134, 57.5], [-139, 59.5], [-146, 60.5], [-152, 59], [-156, 57], [-162, 55.5], [-158, 58], [-162, 60], [-165, 62.5], [-164, 64.5], [-168, 66]]]}}, {"type": "Feature", "id": "greenland", "geometry": {"type": "Polygon", "coordinates": [[[-73, 78], [-60, 82], [-35, 83.5], [-20, 82], [-18, 76], [-22, 70], [-32, 68], [-40, 65], [-43, 60], [-48, 61], [-52, 65], [-54, 69], [-58, 75], [-66, 76.5], [-73, 78]]]}}, {"type": "Feature", "id": "samerica", "geometry": {"type": "Polygon", "coordinates": [[[-77.5, 8.5], [-72, 12], [-66, 10.6], [-61, 10.5], [-58, 7], [-52, 5], [-50, 1], [-44, -2.5], [-35, -5.5], [-35, -9], [-39, -14], [-39.5, -19], [-41, -22.5], [-45, -23.8], [-48.5, -27], [-53, -33.5], [-58, -34.5], [-57.5, -38], [-62, -39], [-65, -42], [-64, -45], [-67.5, -46.5], [-69, -51], [-68.5, -53], [-71, -54], [-74, -50], [-75.5, -46], [-73.5, -40], [-73.5, -37], [-71.5, -30], [-70.5, -24], [-70, -18.5], [-75.5, -15], [-78, -10], [-81, -6], [-80, -2], [-80.5, 0], [-78.5, 2.5], [-77.5, 4], [-77.5, 8.5]]]}}, {"type": "Feature", "id": "africa", "geometry": {"type": "Polygon", "coordinates": [[[-17, 21], [-16, 24], [-13, 27.5], [-9.5, 30], [-6, 35.8], [-2, 35.2], [3, 36.8], [10, 37.2], [11, 33.5], [15, 32.3], [20, 30.8], [20, 32.5], [25, 32], [32, 31.2], [34, 27.5], [35.5, 24], [37.5, 18], [39.5, 15], [43, 12.5], [51, 11.8], [51, 10.5], [48, 5], [43, -1], [40, -3], [39, -7], [40.5, -11], [40.5, -15], [37, -17.5], [35, -21], [35.5, -24], [32.8, -26], [32.5, -29], [30, -31.5], [27, -33.6], [22, -34], [18.5, -34.3], [18, -31.5], [16.5, -28.5], [14.5, -23], [12, -18], [11.8, -15], [13.5, -11], [12.5, -6], [9, -1], [9.5, 3.5], [8.5, 4.5], [5, 6], [1, 6], [-3, 5], [-7.5, 4.4], [-11.5, 7], [-13.5, 9.5], [-15, 11], [-17, 14.7], [-16.5, 19], [-17, 21]]]}}, {"type": "Feature", "id": "madagascar", "geometry": {"type": "Polygon", "coordinates": [[[49.5, -12], [50.5, -15.5], [47.5, -25], [44, -24.5], [43.5, -21], [44.5, -16], [49.5, -12]]]}}, {"type": "Feature", "id": "eurasia", "geometry": {"type": "Polygon", "coordinates": [[[-9.5, 37], [-9, 43], [-1.5, 43.5], [-1, 46], [-4.5, 48], [-1.5, 49.7], [2, 51], [4.5, 53], [8.5, 54], [8.3, 57], [10.5, 57.7], [10.5, 54.4], [14, 54], [19, 54.5], [21, 57], [24, 57.5], [23.5, 59.5], [30, 60], [22, 60.5], [21, 63], [25, 65.5], [21.5, 65.8], [18, 62.5], [17.5, 60.5], [19, 59.8], [16, 56.3], [12.8, 55.5], [11, 59], [5.5, 58.5], [5, 62], [10, 64], [14, 67.5], [19, 70], [25, 71], [30, 70], [41, 67], [44, 68], [54, 68.5], [60, 69.5], [68, 68], [73, 71], [80, 72.5], [87, 74], [97, 76], [105, 77.5], [113, 74], [120, 73], [130, 71], [141, 72.5], [150, 71.5], [160, 69.5], [170, 70], [180, 68.5], [180, 65], [176, 64.5], [178, 62], [170, 60], [163, 60], [163, 57], [162, 54.5], [156, 51], [156, 57], [161, 61.5], [152, 59], [143, 59.5], [137, 54], [141, 53], [140, 48], [135, 43.5], [131, 42.5], [129.5, 40.5], [128, 38.5], [129.4, 35.4], [126.5, 34.5], [126.2, 37.7], [125, 39.5], [121.5, 39], [122, 40.5], [118, 39], [119, 37.3], [122.5, 37], [120.5, 34.5], [121.8, 31], [122, 29], [119.5, 25.5], [116.5, 23], [113, 22.3], [110, 21], [108.5, 21.6], [106.5, 20], [105.7, 18.5], [109, 15.5], [109, 11.5], [105, 8.6], [104.5, 10.5], [103, 10.5], [100.5, 13.5], [99.2, 10], [100.5, 7], [103.5, 1.3], [101, 2.8], [98.3, 8], [98.5, 14], [97.5, 16.5], [94.3, 16], [94, 19], [92, 21.5], [90, 22], [87, 21.5], [86.5, 20], [82, 16.5], [80.2, 13], [79.8, 10.3], [77.5, 8], [76.5, 9], [74.8, 13], [73, 18.5], [72.6, 21.5], [70, 21], [68.5, 23.5], [66.5, 25.4], [61.5, 25.2], [57.3, 25.8], [56.4, 27], [54, 26.7], [51.5, 27.9], [50, 30], [48, 29.9], [48.5, 28], [50.8, 24.8], [51.6, 25.2], [51.5, 24], [54, 24], [56, 26], [57.5, 23.7], [59.8, 22.5], [58.5, 20.5], [57.7, 19], [55.5, 17.7], [52, 16], [48.5, 14], [45, 12.7], [43.3, 12.7], [42.7, 15.6], [40.5, 20], [39, 22.5], [35, 28], [34.4, 28], [32.6, 30], [34.5, 31.5], [35.5, 33.8], [36, 35.8], [32, 36.5], [27.5, 37], [26.2, 39.5], [28, 41], [29, 41.2], [31, 41.1], [36, 41.7], [41.5, 41.5], [39.5, 44], [38, 47], [35, 45], [33.5, 45], [30.5, 46.5], [29.5, 45], [28.7, 44], [28, 42], [24, 40.7], [23, 40], [22.5, 37.5], [21, 38.5], [19.5, 40], [19.5, 42], [16, 43.5], [13.6, 45.5], [12.3, 44.5], [14, 42], [16, 41.4], [18.5, 40.2], [16.5, 38.5], [15.7, 38], [16, 39.5], [12, 42], [10, 44], [8.5, 44.3], [6.5, 43.1], [3, 43.3], [3.2, 42], [0, 39.5], [-0.5, 38], [-2, 36.8], [-5.5, 36], [-6.5, 37], [-9.5, 37]]]}}, {"type": "Feature", "id": "gbritain", "geometry": {"type": "Polygon", "coordinates": [[[-5.7, 50], [1.4, 51.2], [1.7, 52.7], [0, 53.5], [-0.5, 54.5], [-2, 55.8], [-1.8, 57.5], [-4, 57.7], [-3, 58.6], [-5, 58.6], [-6.2, 56.8], [-5.5, 55.3], [-3, 54.8], [-3.2, 53.4], [-4.6, 53.3], [-4.2, 52.3], [-5.2, 51.7], [-3, 51.4], [-5.7, 50]]]}}, {"type": "Feature", "id": "ireland", "geometry": {"type": "Polygon", "coordinates": [[[-6, 52.2], [-6.2, 54], [-5.6, 54.6], [-7.4, 55.3], [-8.5, 54.5], [-10, 54.2], [-9.5, 53], [-10.3, 51.8], [-8, 51.6], [-6, 52.2]]]}}, {"type": "Feature", "id": "iceland", "geometry": {"type": "Polygon", "coordinates": [[[-22.5, 63.8], [-24, 65.5], [-22, 66.4], [-16, 66.5], [-13.5, 65], [-15, 64.3], [-18.7, 63.4], [-22.5, 63.8]]]}}, {"type": "Feature", "id": "honshu", "geometry": {"type": "Polygon", "coordinates": [[[130.9, 34], [132.5, 35.4], [135.5, 35.6], [136.8, 37.2], [138.5, 37.5], [140, 40], [140, 41.4], [141.5, 40.5], [141, 38.3], [140.8, 36], [139.8, 35], [138.8, 34.6], [137, 34.6], [135, 33.8], [132.5, 34.2], [130.9, 34]]]}}, {"type": "Feature", "id": "hokkaido", "geometry": {"type": "Polygon", "coordinates": [[[140, 41.5], [141, 43.2], [141.8, 45.4], [145.5, 43.3], [143.8, 42], [141, 41.8], [140, 41.5]]]}}, {"type": "Feature", "id": "kyushu", "geometry": {"type": "Polygon", "coordinates": [[[129.8, 33.2], [130.9, 33.9], [131.9, 33], [131.3, 31.4], [130.2, 31.2], [129.8, 33.2]]]}}, {"type": "Feature", "id": "taiwan", "geometry": {"type": "Polygon", "coordinates": [[[120.1, 23], [121, 25.2], [122, 25], [121.5, 22.5], [120.7, 22], [120.1, 23]]]}}, {"type": "Feature", "id": "srilanka", "geometry": {"type": "Polygon", "coordinates": [[[79.8, 7.5], [80.2, 9.8], [81.2, 8.5], [81.8, 7], [81, 6], [80, 6], [79.8, 7.5]]]}}, {"type": "Feature", "id": "sumatra", "geometry": {"type": "Polygon", "coordinates": [[[95.3, 5.6], [97.5, 5.2], [100.4, 2.2], [104, -1], [106, -3], [105.8, -5.8], [104.5, -5.9], [102.3, -4], [100, -1.5], [98.6, 1.7], [95.3, 5.6]]]}}, {"type": "Feature", "id": "borneo", "geometry": {"type": "Polygon", "coordinates": [[[109, 1.8], [111, 1.5], [113, 3.2], [116, 6.9], [117.8, 4.3], [118.6, 1], [116.5, -2.5], [116, -3.9], [114.5, -3.6], [111, -3], [110, -1.5], [109, 1.8]]]}}, {"type": "Feature", "id": "java", "geometry": {"type": "Polygon", "coordinates": [[[105.2, -6.8], [108, -6.2], [111, -6.6], [114.5, -7.7], [112.5, -8.4], [108.5, -7.8], [105.2, -6.8]]]}}, {"type": "Feature", "id": "newguinea", "geometry": {"type": "Polygon", "coordinates": [[[131, -1.4], [135, -3.3], [138, -1.6], [141, -2.6], [145, -4.5], [147.5, -6], [147.5, -8], [150, -10.5], [146, -8.5], [143.5, -9], [142.5, -9.3], [140, -8], [138.5, -8.4], [137.5, -5], [134, -4], [131, -1.4]]]}}, {"type": "Feature", "id": "philippines", "geometry": {"type": "Polygon", "coordinates": [[[120.6, 18.5], [122.3, 18.4], [122, 16], [121.6, 14], [124, 12.5], [125.5, 9.5], [126.5, 7], [125.4, 5.6], [122, 7], [123.5, 9], [122, 11.5], [120.5, 14.5], [120.3, 16.5], [120.6, 18.5]]]}}, {"type": "Feature", "id": "australia", "geometry": {"type": "Polygon", "coordinates": [[[113.5, -22], [114, -26.5], [115, -34.2], [118, -35], [123.5, -34], [129, -31.6], [132, -32], [135.5, -34.8], [138, -34.5], [138.5, -35.5], [140.5, -38], [144.5, -38.3], [146.3, -39], [150, -37.5], [151.2, -33.9], [153.1, -30], [153, -25], [149.5, -22.3], [146, -18.5], [145.3, -15], [143.5, -14], [142.4, -10.7], [141.6, -13], [141.5, -17], [139.5, -17.5], [136.5, -15.5], [136.8, -12.2], [132.5, -11.5], [130, -13], [129.5, -15], [126, -14], [122.5, -17], [121, -19.5], [117, -20.6], [113.5, -22]]]}}, {"type": "Feature", "id": "nzn", "geometry": {"type": "Polygon", "coordinates": [[[172.7, -34.4], [174.5, -36], [176, -37.6], [178.5, -37.7], [177, -39.3], [176, -41], [174.8, -41.3], [174.6, -39.5], [173.8, -39.2], [174.5, -38], [172.7, -34.4]]]}}, {"type": "Feature", "id": "nzs", "geometry": {"type": "Polygon", "coordinates": [[[172.7, -40.5], [174, -41.5], [173, -43.7], [171, -45], [169, -46.6], [166.5, -46], [168.5, -44], [171, -42], [172.7, -40.5]]]}}, {"type": "Feature", "id": "cuba", "geometry": {"type": "Polygon", "coordinates": [[[-85, 21.9], [-82, 23.1], [-77.5, 22], [-74.2, 20.2], [-77.5, 19.9], [-80.5, 21.8], [-85, 21.9]]]}}]}, "countries": {"type": "FeatureCollection", "features": [{"type": "Feature", "id": "china", "geometry": {"type": "Polygon", "coordinates": [[[121, 53.3], [126, 52.8], [127.5, 49.8], [131, 47.7], [134.7, 48.3], [133, 45], [131, 44.9], [131, 42.8], [128, 42], [126, 41], [124.3, 39.9], [121.5, 39], [121, 40.5], [119, 39.2], [117.8, 38.8], [118.9, 37.5], [120.8, 37.8], [122.5, 37], [120.3, 35.5], [119.2, 34.5], [120.8, 32.5], [121.9, 31], [122, 29.8], [121.5, 28.3], [120.5, 27.2], [119.5, 25.5], [118, 24.5], [116.5, 23], [114.2, 22.3], [113, 22], [111, 21.5], [110, 20.8], [109.7, 21.6], [108, 21.5], [106.7, 22.8], [105, 23.3], [103.9, 22.6], [102, 22.4], [101.2, 21.3], [99.5, 22.1], [98.7, 24], [97.6, 23.9], [98.7, 27.5], [97.4, 28.3], [96, 29.4], [94, 28], [92, 27.8], [89.5, 28.1], [88.8, 27.4], [88, 27.9], [85, 28.3], [82, 30.2], [80.3, 30.5], [78.8, 31.5], [78.5, 32.7], [79.5, 34.5], [78, 35.5], [76, 35.8], [74.8, 37.2], [73.6, 38.8], [73.8, 39.6], [74.5, 40.5], [76.5, 40.4], [78.5, 41.6], [80.2, 42.1], [80.5, 45], [82.5, 45.3], [83, 47.2], [85.5, 47.1], [87.3, 49.1], [88.2, 48.4], [90.7, 46.0], [91, 45], [93.5, 44.8], [96, 43], [100, 42.6], [104, 41.9], [106.8, 42.3], [110.4, 42.8], [111.9, 43.7], [111.3, 44.8], [113.7, 44.8], [116.7, 46.4], [119.9, 46.7], [117.8, 47.8], [116.3, 49.8], [119.5, 52.6], [121, 53.3]]]}}, {"type": "Feature", "id": "mongolia", "geometry": {"type": "Polygon", "coordinates": [[[87.8, 49.2], [90.7, 50.3], [92.3, 50.8], [97.3, 49.7], [98.2, 52], [102, 51.3], [103.7, 50], [106.9, 50.3], [108.5, 49.4], [111, 49.4], [114.4, 50.3], [116.6, 49.9], [117.8, 47.8], [119.9, 46.7], [116.7, 46.4], [113.7, 44.8], [111.3, 44.8], [111.9, 43.7], [110.4, 42.8], [106.8, 42.3], [104, 41.9], [100, 42.6], [96, 43], [93.5, 44.8], [91, 45], [90.7, 46], [88.2, 48.4], [87.8, 49.2]]]}}, {"type": "Feature", "id": "korea", "geometry": {"type": "Polygon", "coordinates": [[[124.3, 39.9], [126, 41.2], [128, 42], [129.8, 42.6], [130.7, 42.3], [131.5, 40], [130, 35], [127, 33], [124, 34], [124.5, 38], [124.3, 39.9]]]}}, {"type": "Feature", "id": "india", "geometry": {"type": "Polygon", "coordinates": [[[68.2, 23.7], [71, 24.4], [70.3, 28], [73.4, 29.9], [74.6, 31.5], [74.5, 33], [76.8, 35.3], [78, 35.5], [79.5, 34.5], [78.5, 32.7], [78.8, 31.5], [80.3, 30.5], [80.1, 28.8], [84, 27.4], [88, 26.4], [88.8, 27.4], [89.8, 26.7], [92, 26.9], [94, 28], [96, 29.4], [97.3, 28], [95, 26.5], [94.6, 25], [93.2, 22.9], [92.3, 21.5], [91.9, 24.2], [89.8, 25.3], [88.1, 24.5], [88.8, 21.6], [88, 15], [82, 8], [77, 5], [72, 12], [68, 20], [68.2, 23.7]]]}}, {"type": "Feature", "id": "usa", "geometry": {"type": "Polygon", "coordinates": [[[-124.7, 48.4], [-123, 49], [-95.2, 49], [-95, 49.4], [-89.6, 48], [-84.5, 46.5], [-82.5, 45.3], [-82.4, 43], [-79, 43.3], [-76.5, 44.2], [-74.7, 45], [-71.5, 45], [-70, 46.7], [-67.8, 47.1], [-66, 45], [-68, 41], [-73, 38], [-74, 35], [-78, 31], [-79, 27], [-80, 23], [-84, 23.5], [-88, 28], [-94, 27.5], [-97.2, 25.9], [-99.5, 27.5], [-101.4, 29.8], [-103, 29], [-104.6, 29.6], [-106.5, 31.8], [-108.2, 31.8], [-111, 31.3], [-114.8, 32.5], [-117.1, 32.5], [-121, 31], [-126, 38], [-127, 46], [-124.7, 48.4]]]}}, {"type": "Feature", "id": "japan", "geometry": {"type": "Polygon", "coordinates": [[[129, 31], [131, 30], [141, 34], [146, 43], [146, 46], [141, 46], [138, 40], [132, 36], [128.5, 34], [129, 31]]]}}, {"type": "Feature", "id": "gb", "geometry": {"type": "Polygon", "coordinates": [[[-6.5, 49.8], [2, 51], [2, 53], [-1, 56], [-1.5, 59], [-5, 59.2], [-7, 57.5], [-6, 55], [-3.2, 54.8], [-5.5, 53], [-5.8, 51.6], [-6.5, 49.8]]]}}]}, "routes": {"asia": [[[113, 31], [122, 34], [130, 35.5], [138.5, 36.5]], [[113, 31], [120, 37], [127.5, 37]], [[113, 31], [100, 33], [90, 31]], [[113, 31], [109, 25], [106, 17]], [[113, 31], [108, 40], [104, 46]]], "toengland": [[[121, 30.5], [114, 18], [108, 8], [104, 1.5], [96, 5], [82, 5], [66, -6], [52, -20], [40, -30], [24, -37], [14, -30], [8, -12], [2, -2], [-12, 4], [-20, 16], [-17, 30], [-12, 42], [-7, 48], [-1.2, 51]]], "tony": [[[-1.2, 51], [-12, 51], [-28, 49], [-48, 45], [-62, 42.5], [-74, 40.7]]]}, "places": {"china": [113, 31], "japon": [138.5, 36.5], "corea": [127.5, 37], "tibet": [90, 31], "vietnam": [106, 17], "mongolia": [104, 46], "inglaterra": [-1.2, 52], "nuevayork": [-74, 40.7], "india": [79, 22]}}, MT = GD.T;
  const mapEl = document.querySelector('.mapview'), ship = mapEl.querySelector('.mp-ship');
  const G = n => mapEl.querySelector(n), SVGNS = 'http://www.w3.org/2000/svg';
  const gLand = G('.g-land'), gLandC = G('.g-landc'), gBord = G('.g-bord'), gGrat = G('.g-grat'), gHls = G('.g-hls');
  const routesBy = {}; mapEl.querySelectorAll('.mp-route').forEach(r => (routesBy[r.dataset.key] ||= []).push(r));
  const placeEl = {}; mapEl.querySelectorAll('.mp-place').forEach(g => placeEl[g.dataset.p] = g);
  const lerp = (a, b, t) => a + (b - a) * t;
  const hasD3 = typeof d3 !== 'undefined' && d3.geoMercator;
  // world geometry: real country borders (Natural Earth via world-atlas) loaded from the CDN; hand-drawn outlines as a fallback
  const ISO = { china: ['156', 'CN'], gb: ['826', 'GB'], usa: ['840', 'US'], korea: ['410', '408', 'KR', 'KP'], japan: ['392', 'JP'], india: ['356', 'IN'], mongolia: ['496', 'MN'] };
  let world = null, hlEl = {}, mapKey = null, lastP = 0;
  const rewind = f => {
    const g = f.geometry; if (!g) return f;
    const polys = g.type === 'Polygon' ? [g.coordinates] : g.type === 'MultiPolygon' ? g.coordinates : [];
    polys.forEach(p => { if (d3.geoArea({ type: 'Polygon', coordinates: p }) > 2 * Math.PI) p.forEach(r => r.reverse()); });
    return f;
  };
  function useWorld(features, real) {
    const byId = {};
    features.forEach(f => { const id = String(f.id ?? (f.properties && (f.properties.id || f.properties.iso_a2)) ?? ''); byId[id] = f; });
    const hl = {};
    Object.entries(ISO).forEach(([k, ids]) => {
      const fs = real ? ids.map(i => byId[i]).filter(Boolean) : (GD.countries.features.filter(f => f.id === k));
      if (fs.length) hl[k] = { type: 'FeatureCollection', features: fs };
    });
    world = { land: { type: 'FeatureCollection', features }, bord: real ? null : GD.countries, hl, real };
    gHls.innerHTML = ''; hlEl = {};
    Object.keys(hl).forEach(k => { const p = document.createElementNS(SVGNS, 'path'); p.setAttribute('class', 'mp-hl'); gHls.appendChild(p); hlEl[k] = p; });
    if (real) gHls.removeAttribute('clip-path'); else gHls.setAttribute('clip-path', 'url(#g-landclip)');
    if (mapKey !== null) { const k = mapKey; mapKey = null; drawMap(k, lastP); }
  }
  if (hasD3) {
    GD.countries.features.forEach(rewind);
    useWorld(GD.land.features.map(rewind), false);
    const okFeat = fs => Array.isArray(fs) && fs.length > 100 && fs.every(f => { const g = f.geometry; if (!g) return true; let c = g.coordinates; while (Array.isArray(c[0])) c = c[0]; return Math.abs(c[0]) <= 181 && Math.abs(c[1]) <= 91; });
    const idOf = f => { const pr = f.properties || {}; f.id = String(pr['iso-a2'] || pr.iso_a2 || f.id || pr.id || ''); return f; };
    const loadScript = src => new Promise((res, rej) => { const s = document.createElement('script'); s.src = src; s.onload = res; s.onerror = rej; document.head.appendChild(s); });
    const sources = [
      async () => { const [w, tc] = await Promise.all([import('https://cdn.jsdelivr.net/npm/world-atlas@2.0.2/countries-110m.json/+esm'), import('https://cdn.jsdelivr.net/npm/topojson-client@3.1.0/+esm')]);
        const topo = w.default || w; return tc.feature(topo, topo.objects.countries).features.filter(f => f.id !== '010'); },
      async () => { window.Highcharts = window.Highcharts || { maps: {} }; window.Highcharts.maps = window.Highcharts.maps || {};
        await loadScript('https://cdn.jsdelivr.net/npm/@highcharts/map-collection@2.3.3/custom/world.js');
        const gj = window.Highcharts.maps['custom/world']; return gj.features.map(idOf).filter(f => f.id !== 'AQ').map(rewind); },
      async () => { const m = await import('https://cdn.jsdelivr.net/npm/@amcharts/amcharts4-geodata@4.1.31/worldLow.js'); const gj = m.default || m; return gj.features.map(idOf).filter(f => f.id !== 'AQ').map(rewind); },
      async () => { const m = await import('https://cdn.jsdelivr.net/npm/@amcharts/amcharts4-geodata@4.1.31/dist/es2015/worldLow.js'); const gj = m.default || m; return gj.features.map(idOf).filter(f => f.id !== 'AQ').map(rewind); },
    ];
    (async () => {
      for (const src of sources) { try { const fs = await src(); if (okFeat(fs)) { useWorld(fs, true); break; } } catch (e) {} }
    })();
  }
  const proj = hasD3 ? d3.geoMercator().precision(0.3) : null, gp = hasD3 ? d3.geoPath(proj) : null, grat = hasD3 ? d3.geoGraticule().step([15, 15])() : null;
  function camAt(c, p) {
    const L = v => Math.log(v);
    if (p < 0.22) { const t = sm(0, 0.22, p); return [c[0][0], c[0][1], Math.exp(lerp(L(c[0][2] * 1.7), L(c[0][2]), t))]; }
    if (p > 0.78) { const t = sm(0.78, 1, p); return [c[2][0], c[2][1], Math.exp(lerp(L(c[2][2]), L(c[2][2] * 1.7), t))]; }
    const t = sm(0.22, 0.78, p), q = (a, m, b) => { const k = 2 * m - (a + b) / 2; return (1 - t) * (1 - t) * a + 2 * (1 - t) * t * k + t * t * b; };
    return [q(c[0][0], c[1][0], c[2][0]), q(c[0][1], c[1][1], c[2][1]), Math.exp(q(L(c[0][2]), L(c[1][2]), L(c[2][2])))];
  }
  const routeLen = {};
  function along(pts, f) {
    const key = pts.join(';');
    let cum = routeLen[key];
    if (!cum) { cum = [0]; for (let i = 1; i < pts.length; i++) cum.push(cum[i - 1] + d3.geoDistance(pts[i - 1], pts[i])); routeLen[key] = cum; }
    const target = f * cum[cum.length - 1];
    let i = 1; while (i < cum.length - 1 && cum[i] < target) i++;
    const s = (target - cum[i - 1]) / ((cum[i] - cum[i - 1]) || 1);
    return d3.geoInterpolate(pts[i - 1], pts[i])(Math.max(0, Math.min(1, s)));
  }
  function drawMap(k, p) {
    if (!hasD3 || !world) return;
    lastP = p;
    const T = MT[k];
    if (mapKey !== k) {
      mapKey = k;
      mapEl.querySelectorAll('.mp-route').forEach(r => r.style.opacity = 0);
      Object.values(placeEl).forEach(g => { g.style.opacity = 0; g.classList.remove('big'); });
      Object.values(hlEl).forEach(h => h.style.opacity = 0);
    }
    const [lon, lat, z] = camAt(T.cam, p);
    proj.scale(300 * z).translate([0, 0]);
    const c = proj([lon, lat]); proj.translate([756 - c[0], 491 - c[1]]);
    const ld = gp(world.land) || '';
    gLand.setAttribute('d', ld); gLandC.setAttribute('d', ld);
    gGrat.setAttribute('d', gp(grat) || '');
    gBord.setAttribute('d', world.bord ? gp(world.bord) || '' : '');
    const hA = 1 - sm(0.5, 0.66, p), hB = sm(0.6, 0.76, p);
    Object.keys(hlEl).forEach(cn => {
      const o = Math.max(T.hl0.includes(cn) ? hA : 0, T.hl1.includes(cn) ? hB : 0);
      hlEl[cn].style.opacity = o.toFixed(3);
      if (o > 0) hlEl[cn].setAttribute('d', gp(world.hl[cn]) || '');
    });
    const tr = sm(0.3, 0.72, p), rs = routesBy[T.route], RP = GD.routes[T.route];
    rs.forEach((r, i) => {
      r.setAttribute('d', gp({ type: 'LineString', coordinates: RP[i] }) || '');
      r.style.opacity = p > 0.27 ? 1 : 0; r.style.strokeDashoffset = (1 - tr).toFixed(4);
    });
    if (rs.length === 1 && p > 0.27 && tr < 1) {
      const xy = proj(along(RP[0], tr));
      ship.setAttribute('cx', xy[0].toFixed(1)); ship.setAttribute('cy', xy[1].toFixed(1)); ship.style.opacity = 1;
    } else ship.style.opacity = 0;
    T.labels.forEach(n => {
      const g = placeEl[n], pt = GD.places[n];
      const big = (n === T.origin && p < 0.5) || (n === T.dest && p >= 0.5 && T.route !== 'asia');
      g.classList.toggle('big', big);
      const o = n === T.origin ? 1 : n === T.dest ? sm(0.62, 0.72, p) : sm(0.45, 0.6, p);
      g.style.opacity = o.toFixed(3);
      const xy = proj(pt); g.setAttribute('transform', `translate(${xy[0].toFixed(1)},${xy[1].toFixed(1)})`);
    });
  }
  // ---- cover globe
  const cv2 = document.querySelector('.cover2'), cv2T = cv2.querySelector('.cv2-title'), cv2H = cv2.querySelector('.cv2-hint'), cG = cv2.querySelector('.c2-globe');
  const cQ = n => cv2.querySelector(n), cSph = cQ('.c2-sphere'), cHalo = cQ('.c2-halo'), cVol = cQ('.c2-vol'), cRim = cQ('.c2-rim'), cGrat = cQ('.c2-grat'), cLand = cQ('.c2-land'), cHl = cQ('.c2-hl'), cLab = cQ('.c2-lab');
  const cProj = hasD3 ? d3.geoOrthographic().clipAngle(90).precision(0.4) : null, cGp = hasD3 ? d3.geoPath(cProj) : null, cGrid = hasD3 ? d3.geoGraticule10() : null;
  let cLast = -1, cWorld = null;
  function drawCover(p) {
    if (!hasD3 || !world) return;
    if (Math.abs(p - cLast) < 0.0005 && cWorld === world) return; cLast = p; cWorld = world;
    const rise = sm(0.04, 0.34, p), zoom = sm(0.38, 0.86, p);
    const R0 = 330, R = R0 * Math.exp(Math.log(6.5) * zoom * zoom);
    const cy = lerp(982 + R0 * 1.15, 982 * 0.715, rise), y = lerp(cy, 491, sm(0.38, 0.7, p));
    const lon = lerp(62, 104, sm(0.3, 0.8, p)), lat = lerp(22, 33, sm(0.3, 0.8, p));
    cProj.rotate([-lon, -lat]).scale(R).translate([756, y]);
    [cSph, cVol, cRim].forEach(c => { c.setAttribute('cx', 756); c.setAttribute('cy', y.toFixed(1)); c.setAttribute('r', R.toFixed(1)); });
    cHalo.setAttribute('cx', 756); cHalo.setAttribute('cy', y.toFixed(1)); cHalo.setAttribute('r', (R * 1.14).toFixed(1));
    cG.style.opacity = sm(0.0, 0.12, p).toFixed(3);
    cGrat.setAttribute('d', cGp(cGrid) || ''); cLand.setAttribute('d', cGp(world.land) || '');
    const ho = sm(0.45, 0.62, p) * (1 - sm(0.72, 0.86, p)); cHl.style.opacity = ho.toFixed(3);
    if (ho > 0 && world.hl.china) cHl.setAttribute('d', cGp(world.hl.china) || '');
    cLab.style.opacity = ho.toFixed(3);
    if (ho > 0) { const xy = cProj([103, 34.5]); cLab.setAttribute('x', xy[0].toFixed(1)); cLab.setAttribute('y', (xy[1] + 12).toFixed(1)); cLab.setAttribute('font-size', (22 + 30 * zoom).toFixed(1)); }
  }
  function zoomScenes(vh) {
    if (reduce) return;
    const vw = innerWidth, k = Math.max(vw / 1512, vh / 982), ox = (vw - 1512 * k) / 2, oy = (vh - 982 * k) / 2;
    arts.forEach((a, i) => {
      const c = i < cards.length ? rr(i) : (r => ({ top: r.top + vh * 1.1, bottom: r.bottom + vh * 1.1 }))(rr(cards.length - 1));
      let t = Math.max(0, Math.min(1, (vh * 0.8 - c.top) / (vh * 1.05)));
      const e = t * t * (3 - 2 * t), [zx, zy, zs] = ZOOMS[i];
      const f = sceneFade[i] === undefined ? 1 : sceneFade[i], settle = 1 + 0.14 * (1 - f);
      const z = (1 + (zs - 1) * e) * settle;
      const fx = ox + zx * k, fy = oy + zy * k, cx = vw * 0.5, cy = vh * 0.55;
      let tx = fx + (cx - fx) * e - fx * z, ty = fy + (cy - fy) * e - fy * z;
      // keep the zoomed illustration covering the whole screen (no empty edges)
      tx = Math.min(0, Math.max(vw - vw * z, tx));
      ty = Math.min(0, Math.max(vh - vh * z, ty));
      a.style.transform = `translate(${tx.toFixed(1)}px, ${ty.toFixed(1)}px) scale(${z.toFixed(4)})`;
    });
  }
  const _c = 0; const clamp = (v, a, b) => Math.max(a, Math.min(b, v));
  const sm = (a, b, v) => { const t = clamp((v - a) / (b - a), 0, 1); return t * t * (3 - 2 * t); };
  let current = 0, ticking = false;
  // smooth scroll-linked animation: cache card positions and ease a virtual scroll value toward the real one
  let cardTop = [], cardH = [], sy = scrollY;
  const measure = () => { cardTop = cards.map(c => c.getBoundingClientRect().top + scrollY); cardH = cards.map(c => c.offsetHeight); };
  const rr = i => { const top = cardTop[i] - sy; return { top, bottom: top + cardH[i] }; };
  const ccard = document.querySelector('.chartcard'), ccPin = document.querySelector('.cc-pin');
  const CC = {"years": [1908, 1935, 1953, 1960, 1969, 1975, 1985, 1995, 2007, 2025], "series": [[100, 99.9, 99.5, 97, 90, 65, 45, 12, 4, 4], [0, 0.1, 0.5, 3, 10, 35, 55, 88, 96, 96]], "notes": {"1935": "Tetley intenta introducir los primeros saquitos en el Reino Unido sin éxito masivo."}};
  const ctip = ccard.querySelector('.cc-tip');
  const ccRect = document.getElementById('ccrect');
  const ccEnd = ccard.querySelector('.cc-end');
  const CCB = [46, 670, 392, 34], CCB_ = CCB;
  const ccx = yr => CCB[0] + (yr - 1900) / 130 * (CCB[1] - CCB[0]), ccy = v => CCB[2] + v / 100 * (CCB[3] - CCB[2]);
  // light board: a regular grid of little lights; pink ones switch on and grey ones switch off with the real share of each year
  const ccCan = ccard.querySelector('.cc-dots'), ccCtx = ccCan.getContext('2d'), ccSvg = ccard.querySelector('.cc-svg');
  const ccRyr = ccard.querySelector('.cc-ryr'), ccRs = ccard.querySelector('.cc-rs b'), ccRh = ccard.querySelector('.cc-rh b');
  const DOTS = [];
  { let seed = 7; const rnd = () => (seed = (seed * 16807) % 2147483647) / 2147483647;
    const STEP = 9, nx = Math.floor((CCB_[1] - CCB_[0]) / STEP), ny = Math.floor((CCB_[2] - CCB_[3]) / STEP);
    for (let j = 0; j < ny; j++) for (let i = 0; i < nx; i++) {
      const x = CCB_[0] + (i + 0.5) * ((CCB_[1] - CCB_[0]) / nx), y = CCB_[3] + (j + 0.5) * ((CCB_[2] - CCB_[3]) / ny);
      const up = 1 - (y - CCB_[3]) / (CCB_[2] - CCB_[3]);          // 0 at the baseline, 1 at the top
      DOTS.push({ x, y, pink: (i + j) % 2 === 0, rank: 0.55 * up + 0.45 * rnd() });
    } }
  let ccLast = -1, ccW = 0;
  function drawBoard(saq) {
    const w = ccSvg.clientWidth, h = ccSvg.clientHeight, dpr = Math.min(2, devicePixelRatio || 1);
    if (!w) return;
    if (w !== ccW) { ccW = w; ccCan.width = w * dpr; ccCan.height = h * dpr; ccLast = -1; }
    if (Math.abs(saq - ccLast) < 0.0004) return;
    ccLast = saq;
    const k = w / 700, ctx = ccCtx, band = 0.06;
    ctx.setTransform(dpr * k, 0, 0, dpr * k, 0, 0); ctx.clearRect(0, 0, 700, 430);
    for (const d of DOTS) {
      // pink lights switch on below the threshold; grey lights switch off there (same proportion)
      const on = Math.max(0, Math.min(1, (saq - d.rank) / band + 0.5));
      const lit = d.pink ? on : 1 - on;
      ctx.globalAlpha = 0.08 + 0.84 * lit;
      ctx.fillStyle = d.pink ? '#E7503F' : '#4c8fc0';
      ctx.beginPath(); ctx.arc(d.x, d.y, 1.9 + 0.5 * lit, 0, 6.2832); ctx.fill();
    }
    ctx.globalAlpha = 1;
  }
  const ccVal = (s, yr) => { const Y = CC.years, V = CC.series[s]; if (yr <= Y[0]) return V[0];
    for (let i = 1; i < Y.length; i++) if (yr <= Y[i]) { const t = (yr - Y[i-1]) / (Y[i] - Y[i-1]); return V[i-1] + t * (V[i] - V[i-1]); } return V[V.length - 1]; };
  ccard.querySelectorAll('.cc-pt').forEach(p => {
    p.addEventListener('mouseenter', () => {
      const s = +p.dataset.s, i = +p.dataset.i, yr = CC.years[i], note = CC.notes[yr];
      ctip.innerHTML = `<b style="color:${s ? '#E7503F' : '#4c8fc0'}">${s ? 'Té en saquito' : 'Té en hebras'}</b><br><b>${yr}:</b> ${String(CC.series[s][i]).replace('.', ',')} %` + (note ? `<br>${note}` : '');
      const r = p.getBoundingClientRect(), cr = ccard.getBoundingClientRect();
      ctip.style.left = Math.min(cr.width - 260, r.left - cr.left + 16) + 'px'; ctip.style.top = (r.top - cr.top - 14) + 'px'; ctip.style.opacity = 1; });
    p.addEventListener('mouseleave', () => ctip.style.opacity = 0);
  });

  function update() {
    const vh = innerHeight;
    // a scene changes when its card has scrolled completely off the top
    let idx = 0;
    cards.forEach((c, i) => { if (rr(i).bottom <= 0) idx = Math.min(i + 1, scenes.length - 1); });
    // scroll-linked crossfade: the next scene fades in while the current card leaves the top of the screen
    const fade = scenes.map((s, i) => {
      if (i === 0) return 1;
      const r = rr(i - 1);
      const t = Math.max(0, Math.min(1, (vh * 0.45 - r.bottom) / (vh * 0.6)));
      return t * t * (3 - 2 * t);
    });
    // country changes: the scene closes onto the map, the camera travels, then the next scene opens from the map
    const PK = {};
    for (const k in MT) { PK[k] = (vh * 0.55 - rr(k - 1).bottom) / (vh * 1.8); const p = PK[k]; fade[k] = p >= 1 ? 1 : p > 0.78 ? Math.max(0.001, sm(0.78, 1, p)) : 0; }
    scenes.forEach((s, i) => {
      const visible = fade[i] > 0 && !(i + 1 < scenes.length && fade[i + 1] >= 1);
      s.style.opacity = visible ? fade[i].toFixed(3) : 0;
      s.classList.toggle('on', visible);
    });
    let mapP = null;
    const R = Math.hypot(innerWidth, vh) / 2 + 4;
    scenes.forEach(s => { if (s._iris) { s.style.clipPath = ''; s.style.transform = ''; s._iris = 0; } });
    for (const k in MT) {
      const p = PK[k]; if (!(p > 0 && p < 1)) continue;
      mapP = p; drawMap(k, p);
      const out = scenes[k - 1], inn = scenes[k];
      if (p < 0.22) { const e = sm(0, 0.22, p); out.style.transform = `scale(${(1 - 0.12 * e).toFixed(4)})`; out._iris = 1; out.style.opacity = (1 - e).toFixed(3); out.classList.add('on'); }
      else { out.style.opacity = 0; out.classList.remove('on'); }
      if (p > 0.78) { const e = sm(0.78, 1, p); inn.style.transform = `scale(${(1.12 - 0.12 * e).toFixed(4)})`; inn._iris = 1; inn.style.opacity = e.toFixed(3); inn.classList.add('on'); }
      else { inn.style.opacity = 0; inn.classList.remove('on'); }
    }
    mapEl.style.opacity = mapP === null ? 0 : 1;
    if (mapP === null) mapKey = null;
    const mapAct = mapP === null ? 0 : sm(0.08, 0.24, mapP) * (1 - sm(0.8, 0.95, mapP));
    sceneFade = fade;
    current = idx;
    zoomScenes(vh);
    // chapter title: shown centred when a new period starts, cleared as its first card passes over it
    let first = cards.length - 1;
    for (let i = 0; i < cards.length; i++) { if (rr(i).bottom > 0) { first = i; break; } }
    const ch = CARD_CH[first], isFirst = first === 0 || CARD_CH[first - 1] !== ch;
    if (ch !== curCh) { curCh = ch; chYear.textContent = CHS[ch][0]; chSub.textContent = CHS[ch][1]; }
    let op = 0;
    if (isFirst) { const t = rr(first).top; op = Math.max(0, Math.min(1, (t - vh * 0.42) / (vh * 0.36))); }
    // cover: title on paper → the globe rises → zoom into China → the first scene of the timeline
    const cp = Math.max(0, Math.min(1, sy / (vh * 2.2)));
    if (cp < 1) drawCover(cp);
    cv2.style.opacity = (1 - sm(0.8, 1, cp)).toFixed(3); cv2.style.visibility = cp >= 1 ? 'hidden' : '';
    const tUp = sm(0.34, 0.52, cp), tRise = sm(0.04, 0.34, cp);
    cv2T.style.transform = `translate(-50%, calc(-50% - ${(tRise * 24 + tUp * 30).toFixed(2)}vh))`; cv2T.style.opacity = (1 - tUp).toFixed(3);
    cv2H.style.opacity = (0.85 * (1 - sm(0, 0.06, cp))).toFixed(3);
    chapterEl.style.opacity = (op * sm(0.85, 1, cp)).toFixed(3);
    chapterEl.style.transform = `translate(-50%, calc(-50% - ${((1 - op) * 30).toFixed(1)}px - ${(mapAct * 33).toFixed(2)}vh))`;
    { const cr = ccard.getBoundingClientRect();
      // the chart stays pinned on screen; the scroll inside its pin drives the whole animation (and reverses it going back)
      const pr = ccPin.getBoundingClientRect(), span = Math.max(1, pr.height - vh);
      const d = sm(0, 1, (-pr.top + vh * 0.1) / (span * 0.9));
      const Y = CC.years, yr = Y[0] + d * (Y[Y.length - 1] - Y[0]);
      ccRect.setAttribute('width', Math.max(0, ccx(yr) - CCB[0] + 6).toFixed(1));
      { const s = ccVal(1, yr), hb = 100 - s;
        drawBoard(s / 100);
        ccRyr.textContent = Math.round(yr); ccRs.textContent = Math.round(s) + ' %'; ccRh.textContent = Math.round(hb) + ' %'; }
      ccEnd.classList.toggle('on', d >= 1);
    }


    { // the next section pushes in from below and the scene rolls up and compresses, fading at its lower edge
      const at = articleEl.getBoundingClientRect().top, k = Math.max(0, Math.min(1, 1 - at / vh));
      const e = k * k * (3 - 2 * k);
      if (k > 0) {
        const sY = 1 - 0.32 * e, H = Math.max(0, at) / sY, f = vh * 0.16;
        const m = `linear-gradient(to bottom, #000 0, #000 ${Math.max(0, H - f).toFixed(0)}px, transparent ${H.toFixed(0)}px)`;
        stageEl.style.webkitMaskImage = m; stageEl.style.maskImage = m;
        stageEl.style.transform = `scale(1, ${sY.toFixed(4)})`;
      } else { stageEl.style.webkitMaskImage = stageEl.style.maskImage = ''; stageEl.style.transform = ''; }
    }
    hint.style.opacity = scrollY > 40 ? 0 : .8;
  }
  function loop() {
    const target = scrollY, d = target - sy;
    sy = Math.abs(d) < 0.5 ? target : sy + d * 0.14;
    update();
    if (sy !== target) requestAnimationFrame(loop); else ticking = false;
  }
  addEventListener('scroll', () => { if (!ticking) { ticking = true; requestAnimationFrame(loop); } }, { passive:true });
  addEventListener('load', () => { measure(); update(); });
  new ResizeObserver(() => { measure(); update(); }).observe(document.body);
  measure();
  addEventListener('resize', () => { measure(); update(); });
  update();
})();

;

(() => {
  const S = [{"title": "El mundo produce", "unit": "1 taza diaria por cada 100 habitantes del planeta", "perRow": 2, "mult": 1, "vunit": "mil millones de tazas", "labels": ["China", "India", "Indonesia", "Kenia", "Sri Lanka", "Turquía", "Vietnam"], "values": [1493, 629, 63, 285, 139, 140, 96], "icons": [51, 21, 2, 9, 4, 4, 3], "fracs": [1, 1, 1, 1, 1, 1, 1], "daily": [51, 21, 2, 9, 4, 4, 3], "fact": "", "note": "Equivalencia teórica de producción (8.000 millones de habitantes, 365 días), no de consumo real."}, {"title": "El mundo intercambia", "unit": "1 taza diaria por cada 100 habitantes del planeta", "perRow": 1, "mult": 0.3, "vunit": "mil millones de tazas", "labels": ["Argentina", "China", "India", "Kenia", "Sri Lanka", "Vietnam"], "values": [110, 581, 350, 865, 438, 237], "icons": [1, 5, 3, 8, 4, 2], "fracs": [1, 1, 1, 1, 1, 1], "daily": [1, 5, 3, 8, 4, 2], "fact": "", "note": "Equivalencia teórica de exportación (8.000 millones de habitantes, 365 días), no de consumo real."}, {"title": "El mundo consume", "unit": "1 taza por persona al día", "perRow": 1, "mult": 1, "vunit": "tazas al año", "labels": ["Egipto", "Irán", "Irlanda", "Japón", "Marruecos", "Nueva Zelanda", "Polonia", "Reino Unido", "Rusia", "Turquía"], "values": [454, 675, 986, 436, 549, 536, 450, 873, 621, 1422], "icons": [2, 2, 3, 2, 2, 2, 2, 3, 2, 4], "fracs": [1, 1, 1, 1, 1, 1, 1, 1, 1, 1], "daily": [2, 2, 3, 2, 2, 2, 2, 3, 2, 4], "dec": 0, "big": false, "fact": "", "note": "Promedio diario de consumo por habitante de cada país (tazas al año ÷ 365)."}];
  const sec = document.querySelector('.cups'), cv = sec.querySelector('.cups-canvas'), ctx = cv.getContext('2d');
  const titleEl = sec.querySelector('.cups-title'), unitEl = sec.querySelector('.cups-unit');
  const cards = [...sec.querySelectorAll('.cupcard')];
  const N = 94, IDX = [[[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50], [51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71], [72, 73], [74, 75, 76, 77, 78, 79, 80, 81, 82], [83, 84, 85, 86], [87, 88, 89, 90], [91, 92, 93]], [[5], [0, 1, 2, 3, 4], [51, 52, 53], [74, 75, 76, 77, 78, 79, 80, 81], [83, 84, 85, 86], [91, 92]], [[5, 0], [1, 2], [3, 4, 51], [52, 53], [74, 75], [76, 77], [78, 79], [80, 81, 83], [84, 85], [87, 88, 89, 90]]];
  // fraction drawn for each dot in each state (1 = whole cup; the last cup of a country can be partial)
  const FR = S.map((st, k) => { const f = new Float32Array(N).fill(1); IDX[k].forEach((l, c) => { if (l.length) f[l[l.length - 1]] = st.fracs[c]; }); return f; });
  const factEl = sec.querySelector('.cups-fact'), tipEl = sec.querySelector('.cups-tip'), factBig = factEl.querySelector('.cups-fact-big'), factNote = factEl.querySelector('.cups-fact-note');
  let factIdx = 0;
  const setFact = j => { if (j === factIdx) return; factIdx = j; factBig.textContent = S[j].fact || ''; factNote.textContent = S[j].note || ''; };
  function cup(x, y, al, fr, sz) {
    sz = sz || sAll;
    const s = sz * 0.9, x0 = x - s * 0.425, y0 = y - sz * 0.45;
    if (fr >= 0.999) { ctx.globalAlpha = al; ctx.drawImage(sprite, x0, y0, s, s); return; }
    // partial cup: faint whole cup, and the share that counts drawn solid from the left
    ctx.globalAlpha = al * 0.22; ctx.drawImage(sprite, x0, y0, s, s);
    const sw = sprite.width, cut = 0.1 + 0.75 * fr;                 // the cup body spans ~10%–85% of the sprite
    ctx.globalAlpha = al; ctx.drawImage(sprite, 0, 0, sw * cut, sw, x0, y0, s * cut, s);
  }
  // stable pseudo-random per dot
  const rnd = i => { const x = Math.sin(i * 12.9898 + 78.233) * 43758.5453; return x - Math.floor(x); };
  const delay = new Float32Array(N); for (let i = 0; i < N; i++) delay[i] = rnd(i) * 0.45;
  let W = 0, H = 0, OY = 0, layouts = [], dpr = 1, sprite = null, sAll = 6;
  function makeSprite(sz) {
    const px = Math.max(8, Math.round(sz * dpr * 2));    // oversample for crisp edges
    const c = document.createElement('canvas'); c.width = c.height = px;
    const g = c.getContext('2d'), u = px / 20;
    g.strokeStyle = '#567698'; g.lineWidth = 1.0 * u; g.lineJoin = 'round'; g.lineCap = 'round';
    g.beginPath(); g.moveTo(3.5 * u, 5 * u); g.lineTo(13.5 * u, 5 * u); g.lineTo(12.6 * u, 12.8 * u);
    g.quadraticCurveTo(12.1 * u, 15 * u, 9.8 * u, 15 * u); g.lineTo(7.2 * u, 15 * u);
    g.quadraticCurveTo(4.9 * u, 15 * u, 4.4 * u, 12.8 * u); g.closePath(); g.fillStyle = '#E7EEF8'; g.fill(); g.stroke();
    g.beginPath(); g.arc(14 * u, 8.8 * u, 2.4 * u, -Math.PI / 2.2, Math.PI / 2.2); g.stroke();
    g.beginPath(); g.moveTo(2 * u, 17.4 * u); g.lineTo(15 * u, 17.4 * u); g.stroke();
    g.beginPath(); g.moveTo(7 * u, 3.2 * u); g.quadraticCurveTo(6 * u, 2 * u, 7 * u, 0.8 * u); g.moveTo(10 * u, 3.2 * u); g.quadraticCurveTo(9 * u, 2 * u, 10 * u, 0.8 * u); g.stroke();
    return c;
  }

  function layout() {
    dpr = Math.min(2, devicePixelRatio || 1);
    W = cv.clientWidth; H = innerHeight; OY = H;
    cv.width = W * dpr; cv.height = cv.clientHeight * dpr;
    const top = H * 0.32, bottom = H * 0.92, left = Math.max(60, W * 0.06), right = W - Math.max(60, W * 0.06);
    // one dot size for every chart: the largest that lets all three fit
    const fit = st => Math.min((bottom - top) / Math.ceil(Math.max(...st.icons) / st.perRow), (right - left) / st.icons.length * 0.86 / st.perRow);
    sAll = Math.min(...S.map(fit));  // the same cup size in the three charts
    const sBig = st => Math.min((right - left) / st.icons.length * 0.62, (bottom - top - 40) / Math.max(...st.icons) * 0.92);
    sprite = makeSprite(sAll);
    layouts = S.map((st, k) => {
      const C = st.values.length, colW = (right - left) / C;
      // production and exports share the same scale so the bars visibly shrink
      const s = sAll;
      const pos = new Float32Array(N * 2).fill(NaN), owner = new Int16Array(N).fill(-1), bottoms = [];
      st.icons.forEach((v, c) => {
        const x0 = left + c * colW + (colW - st.perRow * s) / 2;
        IDX[k][c].forEach((i, j) => {
          const r = Math.floor(j / st.perRow), q = j % st.perRow;
          pos[i * 2] = x0 + q * s + s / 2; pos[i * 2 + 1] = top + r * s + s / 2; owner[i] = c;
        });
        bottoms.push(top + Math.ceil(v / st.perRow) * s);
      });
      return { pos, owner, s, colW, left, top, C, bottoms };
    });
  }

  // one label size per chart: the largest size at which every country fits its column,
  // allowing names with two words to wrap onto two lines
  const labelCache = new Map();
  function lines(lab, maxW) {
    if (ctx.measureText(lab).width <= maxW) return [lab];
    const w = lab.split(' ');
    if (w.length < 2) return null;
    let best = null;
    for (let i = 1; i < w.length; i++) {
      const a = w.slice(0, i).join(' '), b = w.slice(i).join(' ');
      if (ctx.measureText(a).width <= maxW && ctx.measureText(b).width <= maxW) { best = [a, b]; break; }
    }
    return best;
  }
  function labelLayout(st, L) {
    const key = st.title + '|' + Math.round(L.colW);
    if (labelCache.has(key)) return labelCache.get(key);
    const maxW = L.colW * 0.9;
    let size = 16, out = null;
    for (; size >= 9; size -= 0.5) {
      ctx.font = `700 ${size}px 'Aleo', Georgia, serif`;
      const ls = st.labels.map(l => lines(l.toUpperCase(), maxW));
      if (ls.every(Boolean)) { out = { size, ls }; break; }
    }
    if (!out) { ctx.font = `700 9px 'Aleo', Georgia, serif`; out = { size: 9, ls: st.labels.map(l => [l.toUpperCase()]) }; }
    labelCache.set(key, out);
    return out;
  }
  function guide(cx, L, c) {
    ctx.save(); ctx.strokeStyle = 'rgba(35,55,75,.35)'; ctx.lineWidth = 1; ctx.setLineDash([1.5, 3]);
    ctx.beginPath(); ctx.moveTo(Math.round(cx) + .5, L.top - 10); ctx.lineTo(Math.round(cx) + .5, H * 0.95); ctx.stroke(); ctx.restore();
  }
  function drawNum(txt, cx, L) {
    ctx.textAlign = 'center'; ctx.font = "700 26px 'Bree Serif', Georgia, serif"; ctx.fillStyle = '#4c8fc0';
    ctx.fillText(txt, cx, L.top - 14); ctx.textAlign = 'start';
  }
  function drawLabel(lab, cx, L, st, c) {
    const lay = labelLayout(st, L), ls = lay.ls[c], lh = lay.size * 1.15;
    ctx.font = `700 ${lay.size}px 'Aleo', Georgia, serif`;
    ctx.fillStyle = '#1f2024'; ctx.textAlign = 'center'; ctx.textBaseline = 'alphabetic';
    ls.forEach((t, j) => ctx.fillText(t, cx, L.top - 44 - (ls.length - 1 - j) * lh));
    ctx.textAlign = 'start';
  }
  const ease = t => t < .5 ? 4 * t * t * t : 1 - Math.pow(-2 * t + 2, 3) / 2;
  const clamp = (v, a, b) => Math.max(a, Math.min(b, v));

  function stateAt() {
    // morph k→k+1 runs while card k leaves the top of the screen
    const vh = innerHeight;
    for (let k = 0; k < cards.length; k++) {
      const r = cards[k].getBoundingClientRect();
      if (k === cards.length - 1) return { k: Math.min(k, S.length - 1), m: 0 };
      if (r.bottom > -vh * 0.15) {
        const m = clamp((vh * 0.35 - r.bottom) / (vh * 0.5), 0, 1);
        return { k, m };
      }
    }
    return { k: S.length - 1, m: 0 };
  }

  // intro: a few loose cups float while the section scrolls in, then fly into the first chart
  const subset = new Uint8Array(N); for (let i = 0; i < N; i++) subset[i] = rnd(i + 31) < 0.16 ? 1 : 0;
  let t0 = performance.now(), looping = false;
  function introProgress() {
    const r = sec.getBoundingClientRect();
    return { a: clamp((innerHeight * 0.5 - r.top) / (innerHeight * 0.7), 0, 1), visible: r.top < innerHeight * 2 && r.bottom > 0 };
  }
  function drawIntro(a) {
    const L = layouts[0], time = (performance.now() - t0) / 1000;
    ctx.setTransform(dpr, 0, 0, dpr, 0, OY * dpr); ctx.clearRect(0, -OY, W, H + OY);
    S[0].labels.forEach((_, c) => guide(L.left + c * L.colW + L.colW / 2, L, c));
    for (let i = 0; i < N; i++) {
      const bx = L.pos[i * 2], by = L.pos[i * 2 + 1];
      if (bx !== bx) continue;
      let x, y, al;
      if (subset[i]) {
        const sx = 30 + rnd(i + 101) * (W - 60);
        const sy = -H * 0.19 + rnd(i + 202) * H * 0.21;
        const t = ease(clamp((a - delay[i] * 0.6) / 0.6, 0, 1));
        const base = rnd(i + 303) < 0.35 ? 0.35 : 1;          // some cups lighter, like the reference
        x = sx + (bx - sx) * t; y = sy + (by - sy) * t; al = base + (1 - base) * t;
      } else {
        const t = ease(clamp((a - 0.55 - delay[i] * 0.4) / 0.3, 0, 1));
        x = bx; y = by - (1 - t) * 90; al = t;
      }
      if (al <= 0.01) continue;
      cup(x, y, al, FR[0][i]);
    }
    const la = 1;
    if (la > 0.01) {
      ctx.globalAlpha = la;
      S[0].labels.forEach((lab, c) => {
        const cx = L.left + c * L.colW + L.colW / 2;
        drawLabel(lab, cx, L, S[0], c);
      });
    }
    ctx.globalAlpha = 1;
    titleEl.textContent = S[0].title; unitEl.textContent = S[0].unit;
    titleEl.style.opacity = unitEl.parentNode.style.opacity = la;
    setFact(0); factEl.style.opacity = la; curState = a > 0.95 ? 0 : -1;
  }
  // tooltip on the production chart: the daily figure per 100 people and the annual production it comes from
  let curState = -1;
  sec.addEventListener('mousemove', ev => {
    if (curState < 0) { tipEl.style.opacity = 0; return; }
    const L = layouts[curState], st = S[curState];
    if (!L) { tipEl.style.opacity = 0; return; }
    const r = sec.querySelector('.cups-stage').getBoundingClientRect(), x = ev.clientX - r.left, y = ev.clientY - r.top;
    const c = Math.floor((x - L.left) / L.colW);
    if (c < 0 || c >= st.labels.length || y < L.top - 40 || y > L.bottoms[c] + 30) { tipEl.style.opacity = 0; return; }
    const d = st.daily[c].toLocaleString('es-AR', { minimumFractionDigits: st.dec || 0, maximumFractionDigits: st.dec || 0 });
    tipEl.innerHTML = curState === 2
      ? `<b>${st.labels[c]}</b><br><b>${d}</b> tazas por persona al día<br>${st.values[c].toLocaleString('es-AR')} tazas por persona al año`
      : `<b>${st.labels[c]}</b><br><b>${d}</b> tazas diarias por cada 100 habitantes del planeta<br>${(Math.round(st.values[c] * st.mult * 10) / 10).toLocaleString('es-AR')} mil millones de tazas ${curState === 0 ? 'producidas' : 'exportadas'} al año`;
    tipEl.style.left = Math.min(r.width - 270, x + 16) + 'px'; tipEl.style.top = (y - 10) + 'px'; tipEl.style.opacity = 1;
  });
  sec.addEventListener('mouseleave', () => tipEl.style.opacity = 0);

  function draw() {
    const ip = introProgress();
    if (ip.a < 1) {
      drawIntro(ip.a);
      return;
    }
    const { k, m } = stateAt();
    const A = layouts[k], B = layouts[Math.min(k + 1, S.length - 1)];
    ctx.setTransform(dpr, 0, 0, dpr, 0, OY * dpr);
    ctx.clearRect(0, -OY, W, H + OY);
    // dotted guide under every country (crossfading between charts)
    ctx.globalAlpha = 1 - m; S[k].labels.forEach((_, c) => guide(A.left + c * A.colW + A.colW / 2, A, c));
    if (k < S.length - 1) { ctx.globalAlpha = m; S[k + 1].labels.forEach((_, c) => guide(B.left + c * B.colW + B.colW / 2, B, c)); }
    ctx.globalAlpha = 1;
    ctx.fillStyle = '#d6383a';
    const rA = A.s * 0.36, rB = B.s * 0.36;
    for (let i = 0; i < N; i++) {
      const ax = A.pos[i * 2], ay = A.pos[i * 2 + 1], bx = B.pos[i * 2], by = B.pos[i * 2 + 1];
      const inA = ax === ax, inB = bx === bx;
      if (!inA && !inB) continue;
      const t = ease(clamp((m - delay[i]) / 0.55, 0, 1));
      let x, y, a, r;
      if (inA && inB) { x = ax + (bx - ax) * t; y = ay + (by - ay) * t - Math.sin(Math.PI * t) * 60 * (rnd(i + 7) - .3); a = 1; r = rA + (rB - rA) * t; }
      else if (inA) { x = ax; y = ay + t * 140; a = 1 - t; r = rA; }      // dot leaves (falls and fades)
      else { x = bx; y = by - (1 - t) * 120; a = t; r = rB; }            // dot arrives (drops in)
      if (a <= 0.01) continue;
      const fa = inA ? FR[k][i] : 1, fb = inB ? FR[Math.min(k + 1, S.length - 1)][i] : 1;
      cup(x, y, a, inA && inB ? fa + (fb - fa) * t : inA ? fa : fb, inA && inB ? A.s + (B.s - A.s) * t : inA ? A.s : B.s);
    }
    ctx.globalAlpha = 1;
    // country names crossfade; amounts appear under each column only once it is assembled
    const fmt = (st, v, c) => { if (st.daily) return st.daily[c].toLocaleString('es-AR', { minimumFractionDigits: st.dec || 0, maximumFractionDigits: st.dec || 0 }); const x = v * st.mult; return (x >= 100 || st.mult === 1 ? Math.round(x) : Math.round(x * 10) / 10).toLocaleString('es-AR'); };
    [[A, S[k], 1 - m, 1 - clamp(m * 5, 0, 1)], [B, S[Math.min(k + 1, S.length - 1)], m, clamp((m - .9) * 10, 0, 1)]].forEach(([L, st, al, va], side) => {
      if (side === 1 && k === S.length - 1) return;
      st.labels.forEach((lab, c) => {
        const cx = L.left + c * L.colW + L.colW / 2;
        if (al > .02) {
          ctx.globalAlpha = al;
          drawLabel(lab, cx, L, st, c);
        }
        if (va > .02) {
          ctx.globalAlpha = va; ctx.textAlign = 'center';
          drawNum(fmt(st, st.values[c], c), cx, L);
          ctx.textAlign = 'start';
        }
      });
    });
    ctx.globalAlpha = 1;
    const cur = m < .5 ? S[k] : S[Math.min(k + 1, S.length - 1)];
    if (titleEl.textContent !== cur.title) { titleEl.textContent = cur.title; unitEl.textContent = cur.unit; }
    const f = Math.abs(m - .5) * 2; titleEl.style.opacity = unitEl.parentNode.style.opacity = (m > 0 && m < 1) ? Math.max(.15, f) : 1;
    const cj = m < .5 ? k : Math.min(k + 1, S.length - 1); setFact(cj);
    factEl.style.opacity = (S[cj].note ? ((m > 0 && m < 1) ? Math.max(0, f * 1.2 - .2) : 1) : 0).toFixed(3);
    curState = (k === 0 && m < 0.05) ? 0 : (m < .05 ? k : m > .95 ? k + 1 : -1);
  }

  let tick = false;
  const req = () => { if (!tick) { tick = true; requestAnimationFrame(() => { tick = false; draw(); }); } };
  addEventListener('scroll', req, { passive: true });
  addEventListener('resize', () => { labelCache.clear(); layout(); draw(); });
  layout(); draw();
  document.fonts && document.fonts.ready.then(() => { labelCache.clear(); draw(); });
})();

(() => {
  const DATA = {"calma": {"sky": ["#e9eee8", "#f1ede2", "#efd3a6", "#cfd6cc"], "teas": ["#ece3b8", "#9a5a2e", "#c8b46a"]}, "equilibrio": {"sky": ["#ece9e0", "#e8e4d4", "#dfe6d6", "#f2e4b8"], "teas": ["#c99a4a", "#b9c87a", "#e6cf6a"]}, "energia": {"sky": ["#f6e0b6", "#e4edcc", "#f3d8ae", "#d8c6ae"], "teas": ["#8ab24a", "#8a3a1e", "#4a2a1a"]}, "renovacion": {"sky": ["#e7f0da", "#e4efdc", "#e3e5ee", "#f0e8cc"], "teas": ["#c6d27a", "#e2d79a", "#d6c07a"]}};
  const hex = h => [1, 3, 5].map(i => parseInt(h.slice(i, i + 2), 16));
  const mix = (a, b, t) => { const A = hex(a), B = hex(b); return `rgb(${A.map((v, i) => Math.round(v + (B[i] - v) * t)).join(',')})`; };
  const clamp = (v, a, b) => Math.max(a, Math.min(b, v));
  const sm = t => t * t * (3 - 2 * t);
  const open = {};
  document.querySelectorAll('.journey').forEach(jr => {
    const D = DATA[jr.dataset.key], sc = jr.querySelector('.jr-scroll'), track = jr.querySelector('.jr-track');
    const sky = jr.querySelector('.jr-sky'), walker = jr.querySelector('.jr-walker'), tea = walker.querySelector('.jr-tea');
    const dots = [...jr.querySelectorAll('.jr-dots i')], back = jr.querySelector('.jr-back');
    let walkT = 0, cur = -1;
    function update() {
      const max = sc.scrollHeight - sc.clientHeight, p = max > 0 ? sc.scrollTop / max : 0, seg = p * 3;
      track.style.transform = `translateX(${-seg * 100}vw)`;
      const i = Math.min(3, Math.floor(seg)), f = sm(clamp((seg - i - .55) / .45, 0, 1));
      sky.style.background = jr.style.background = mix(D.sky[i], D.sky[Math.min(3, i + 1)], f);
      walker.style.left = '50%';
      const k = clamp(Math.round(seg) - 1, 0, 2);
      if (k !== cur) { cur = k; if (tea) tea.setAttribute('fill', D.teas[k]); dots.forEach((d, j) => d.classList.toggle('on', j === k)); }
      walker.classList.add('walking'); clearTimeout(walkT); walkT = setTimeout(() => walker.classList.remove('walking'), 180);
    }
    sc.addEventListener('scroll', () => requestAnimationFrame(update), { passive: true });
    const close = () => { jr.classList.remove('open'); jr.setAttribute('aria-hidden', 'true'); document.body.classList.remove('jr-lock');
      document.querySelector('.paths').scrollIntoView({ block: 'center' }); };
    back.addEventListener('click', close);
    jr._close = close;
    open[jr.dataset.key] = () => { sc.scrollTop = 0; cur = -1; update(); walker.classList.remove('walking');
      jr.classList.add('open'); jr.setAttribute('aria-hidden', 'false'); document.body.classList.add('jr-lock');
      setTimeout(() => back.focus({ preventScroll: true }), 650); };
  });
  addEventListener('keydown', e => { if (e.key === 'Escape') { const o = document.querySelector('.journey.open'); if (o) o._close(); } });
  document.querySelectorAll('.ch').forEach(btn => {
    const key = btn.getAttribute('aria-label').normalize('NFD').replace(/[̀-ͯ]/g, '').toLowerCase();
    if (!open[key]) return;
    btn.addEventListener('click', () => { btn.classList.add('jumping'); setTimeout(() => { btn.classList.remove('jumping'); open[key](); }, 520); });
  });
})();
