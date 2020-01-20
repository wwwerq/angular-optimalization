title: How to optimize an Angular app
speaker: Weronika
plugins:
    - echarts



<slide class="bg-black-blue aligncenter" image="https://images.pexels.com/photos/97077/pexels-photo-97077.jpeg?auto=compress&cs=tinysrgb&dpr=3&h=750&w=1260 .dark">

# How to optimize an Angular app {.text-landing.text-shadow}


Weronika Szymańska<br><br>
<img src="https://anstatic.azureedge.net/assets/images/logo.svg?v=1.2.7"/>


<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li class="animated fadeInUp tobuild">Code minification</li>
</ol>



<slide class="bg-black-blue" .dark">
## Code minification
<ul>
    <li class="animated fadeInUp tobuild">remove whitespace</li>
    <li class="animated fadeInUp tobuild">remove functions that are never executed</li>
    <li class="animated fadeInUp tobuild">change functions' and variables' names to shorter ones</li>
    <li class="animated fadeInUp tobuild">uglifyJS, minifyCSS........</li>
</ul>

<p class="animated fadeInUp tobuild">...but</p>
## FORGET ABOUT IT {.animated.fadeInUp.tobuild}
<p class="animated fadeInUp tobuild">we have angular and we have `ng build --prod`</p>
<a href="https://github.com/angular/angular-cli/tree/master/packages/angular_devkit/build_optimizer" class="animated fadeInUp tobuild">https://github.com/angular/angular-cli/tree/master/packages/angular_devkit/build_optimizer</a>



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li class="animated fadeInUp tobuild">OnPush Change Detection</li>
</ol>



<slide class="bg-black-blue fullscreen"">
<img class="aligncenter" src="https://previews.dropbox.com/p/thumb/AArqEgV96DATTDfhoOfQjPTnuhrkuYttjTySALhxAorlABoKC9GVMUaj-obu6oMIQmmeluQGXthjyXjtVKwtybjYjDuCdpEWVvewk03QZUAwA4MtUAPgv17EJ-X7I33BBGL-xRlqd7TD-Ko4ZNFgCxdpnSRCfZ7YdFm1FXtmfexKdJuMexhMcmKK3ECCIc6Ypitfz8H9DfFbQXi8ZQQhnOHAJmQ_bpUgH0v6OBh4xTq_czGL9lqu8mnVsLUcfaBo1Ng4utI9qEHc-8tn2UdptORhIERzlpnEkJHU2HRwnclqaw9lPzXobCvJsxIBe7aEEj3o3V8MBsZJ5dT9q0-5Aeh-/p.png?fv_content=true&size_mode=5">



<slide class="bg-black-blue fullscreen"">
<img class="aligncenter" src="https://previews.dropbox.com/p/thumb/AArkXLST9x8nE08PPPrym0VfZD-tCMOu1c8T60yDh1EkCe8UfwqYHrWp40FjxtoILWn7Y9fclYINulB34q9rI5Beu0f88tXL5i6oybhALGNo7oc5FC6iX8F0w_V-lLr_jioL6sQp51t3PIqgMLdj07r7BwOvM7fvUBueK7vV8ZSh0dla--XUeFfszGHg9VE3nSdcP86Ar5GbpGiPgYFyUQF_4bVL82OOkbTQk9WzuwoWkdRQngtRGUPDUHS8rgh72cD_UKKd9Zjqn2T8UBnyDw4W0H75yXawgBXA6FhhVT0GSCl2KVY2vwfVZ6UQ03fSyPgUql75Wy2vBdJWDrXj1Wgk/p.png?fv_content=true&size_mode=5">



<slide class="bg-black-blue fullscreen"">
<img class="aligncenter" src="https://previews.dropbox.com/p/thumb/AApy2SEFdsWGoqNlLefCgqg2x2MSAON1MsryjQ_JGPMfHWzCpV62HrKlS38DU3rkEvCZGOPvhJWTYWgqZeIbEw9tvZ3coA71OxK49P4ge7iNcEwU_Iw8F01Yc6HUXQ1KbMI-zuyHMqtLe8t8Pt8litMaOuYs7X_OY_EKDAu4zmhs4KRcFkwes_3J7alYaXAlQ4YOhU6wpc4q07yoX2OGsA-JVKa_cmBfyWS7D8pk4ROfbJi7m-wFCBB0EoF_rvrtmt810F1VGLiA4oPDrWtM5ZcrVinZBCNx71ZyVnJPTvd8Tk6SoY4o6f-LZtEmGgcMJwDBiZwnHfI2NQUbTbwGZbTU/p.png?fv_content=true&size_mode=5">



<slide class="bg-black-blue" .dark">
@Component({<br>
&nbsp;&nbsp;&nbsp;...<br>
&nbsp;&nbsp;&nbsp;changeDetection: ChangeDetectionStrategy.OnPush<br>
})<br>
export class Component {<br>
&nbsp;&nbsp;&nbsp;@Input() name;<br>
}


<slide class="bg-black-blue" .dark">
## OnPush works by comparing references of the inputs of the component

<br>
<div class="tobuild">
    <p>{{ name }}</p>
</div>
<br><br>
<div class="tobuild">
    changeName(): void {<br>
    &nbsp;&nbsp;&nbsp;this.name = 'Andrzej';<br>
    }
</div>



<slide class="bg-black-blue fullscreen"">
<img class="aligncenter" src="https://previews.dropbox.com/p/thumb/AArpF9vqSdGVEhuF1df7BDS4DW8w8KbuXNQcv8EEHlaV2J_AdNvNRTy49Sb0VqbJClU3AXfo6GDmCIIVPeuJR6IFaqszOREsn34Ah2n59If_lZZZgNlGaqFzyZ7YTY6SNz8cwJi2M1dfMkayeCQswNJpequMsVddnfh7v2b4E2aneWe8kWcS2pusYNTz77CqN0y45hkZy1Yr7AyTZfB5bRbr8W8HRyHd3GfHjZDswsdHTcaGeoXUkaicV4_eV4l73Ck2oLCZ5pOcj_RJFDJaoDERX-wRnxfRoXt9zLAUMuN8s0SXGQOa29DCDrC8XPwKM9GxVSLTsY8tKnIacK3ZCTtC/p.png?fv_content=true&size_mode=5">



<slide class="bg-black-blue fullscreen"">
<img class="aligncenter" src="https://previews.dropbox.com/p/thumb/AArd697RqPkylvs4-3XViXORYkiZm_1WKS8JbHLoRhkihl0uIv0YPQh2dwfNdaGVNAeSymDsdRVrf3mEdBrqMm51NxStnzNlQ8O6fb9Xxcr_cZO3tVB-o7eQSYhOqdWKiGLaAjIGjU5wsEu1TqJTtYW05jVgfRos3Mo30NVbWpvgsY36OfwEtDvKtgfPH3Mb-zVVkvx1w7OQqMVbofCDgsTMEyFO74Yvp0h6qnLVJmDITOzgC7HrmVAlxuUN_3zrOSKfDnWBUy75fQP56FAb68wOCUfWFSN42-YG_wVrr_CEmtTxw9ffx6db3-v6l7xv0SVZiXUw0BiC3NzxHJDlqRZN/p.png?fv_content=true&size_mode=5">



<slide class="bg-black-blue" .dark">
## Change detector for component with OnPush Strategy will be trigger only when...

<p class="animated fadeInUp tobuild">... value in @Input() has been changed</p>
<p class="animated fadeInUp tobuild">... an event has been emitted by template</p>
<p class="animated fadeInUp tobuild">... an event has been triggered by Observable in this component</p>
<p class="animated fadeInUp tobuild">... `this.changeDetector.markForCheck()` has been called</p>



<slide class="bg-black-blue fullscreen"">
<img class="aligncenter" src="https://previews.dropbox.com/p/thumb/AAod2Q-wHb8oZC5IGiQQbhRXoS3XBpjI4IB349_7l2N9CCqeE8ml-0K9be2O6Znn735a3ShNBFFANELjLGsvWfLZEwWWDgkJ7bapBzA_UNnoqFCdFX6J-lypHodSz7kpfiphlL2Cc9fRLo8Cxe7qEnE2EQC7WcUd2UHGl0v02quCTkqktqEhB4iFPXh4xBpbI25WLjuZIZXGwFDSfqTwR1sPmfFc8-ZS-_JChozDKMx_Rg0Be9rsqDByVAE3lEVn8x91LqdqhVH_EwK_U3OKIhSv63QcVnG-TQgjjQg3EdUl6am4apxQMaKnZE6vjDleRhoYn9585fw4TGhqoCF3vjGG/p.png?fv_content=true&size_mode=5">



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li class="animated fadeInUp tobuild">Pure pipes instead of functions/getters in templates</li>
</ol>



<slide class="bg-black-blue" .dark">
## Pure pipes
<br>
<br>
class foo {<br>
&nbsp;&nbsp;&nbsp;private _bar: boolean = false;<br>
&nbsp;&nbsp;&nbsp;get bar(): boolean {<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return this._bar;<br>
&nbsp;&nbsp;&nbsp;}<br>
}
<br>
<br>
`get` used in the view is nothing more than a function call.<br>
Pure pipes will always return the same output, no matter how many times they will receive the same input. <br>
If the change detector reaches this view and `pure` in the pipe is set to `true`, <br>
the change detector will not check if that value has been changed because it knows that it will return exactly the same value.



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li class="animated fadeInUp tobuild">async pipe</li>
</ol>



<slide class="bg-black-blue" .dark">
## async pipe

The async pipe allows for subscribe to Observable directly from the template.<br>
With async pipe, there's no need to care about unsubscribing,<br>
moreover Change Detector will check if the value has been changed only when Observable changed itself.



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li>async pipe</li>
    <li class="animated fadeInUp tobuild">Unsubscribe</li>
</ol>



<slide class="bg-black-blue" .dark">
## Unsubscribe (1st method)

let sub1: Subscription;<br>
let sub2: Subscription;<br>

ngOnInit() {<br>
&nbsp;&nbsp;&nbsp;this.sub1 = this.service.Subject1.subscribe(() => {});<br>
&nbsp;&nbsp;&nbsp;this.sub2 = this.service.Subject2.subscribe(() => {});<br>
}<br>

ngOnDestroy() {<br>
&nbsp;&nbsp;&nbsp;if (this.sub1) {<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;this.sub1.unsubscribe();<br>
&nbsp;&nbsp;&nbsp;}<br>
&nbsp;&nbsp;&nbsp;if (this.sub2) {<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;this.sub2.unsubscribe();<br>
&nbsp;&nbsp;&nbsp;}<br>
}<br>


<slide class="bg-black-blue" .dark">
## Unsubscribe (2nd method)

let subs: Subscription[] = [];<br>
 
ngOnInit() {<br>
&nbsp;&nbsp;&nbsp;this.subs.push(this.service.Subject1.subscribe(() => {}));<br>
&nbsp;&nbsp;&nbsp;this.subs.push(this.service.Subject2.subscribe(() => {}));<br>
}
 
ngOnDestroy() {<br>
&nbsp;&nbsp;&nbsp;subs.forEach(sub => sub.unsubscribe());<br>
}



<slide class="bg-black-blue" .dark">
## Unsubscribe (3rd method)

private subscriptions = new Subscription();<br>
 
ngOnInit() {<br>
&nbsp;&nbsp;&nbsp;this.subscriptions.add(this.service.Subject1.subscribe(() => {}));<br>
&nbsp;&nbsp;&nbsp;this.subscriptions.add(this.service.Subject2.subscribe(() => {}));<br>
}<br>
 
ngOnDestroy() {<br>
&nbsp;&nbsp;&nbsp;this.subscriptions.unsubscribe();<br>
}



<slide class="bg-black-blue" .dark">
## Unsubscribe (4th method)

ngUnsubscribe = new Subject<void>();<br>
 
ngOnInit() {<br>
&nbsp;&nbsp;&nbsp;this.service.Subject1.pipe(takeUntil(this.ngUnsubscribe))<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.subscribe(() => {});<br>
&nbsp;&nbsp;&nbsp;this.service.Subject2.pipe(takeUntil(this.ngUnsubscribe))<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.subscribe(() => {});<br>
}<br>

ngOnDestroy(): void {<br>
&nbsp;&nbsp;&nbsp;this.ngUnsubscribe.next();<br>
&nbsp;&nbsp;&nbsp;this.ngUnsubscribe.complete();<br>
}



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li>async pipe</li>
    <li>Unsubscribe</li>
    <li class="animated fadeInUp tobuild">Track By function</li>
</ol>



<slide class="bg-black-blue" .dark">
## `Track by` function
<br><br>
*ngFor="let document of documents; trackBy: trackByFn"




<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li>async pipe</li>
    <li>Unsubscribe</li>
    <li>Track By function</li>
    <li class="animated fadeInUp tobuild">Webpack Bundle Analyzer</li>
</ol>



<slide class="bg-black-blue fullscreen" .dark">
## Webpack Bundle Analyzer {.aligncenter}

<img class="aligncenter" src="https://cloud.githubusercontent.com/assets/302213/20628702/93f72404-b338-11e6-92d4-9a365550a701.gif">



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li>async pipe</li>
    <li>Unsubscribe</li>
    <li>Track By function</li>
    <li>Webpack Bundle Analyzer</li>
    <li class="animated fadeInUp tobuild">You (might) not need</li>
</ol>



<slide class="bg-black-blue" .dark">
## You (might) not need
<a target="_blank" href="https://youmightnotneed.com/">https://youmightnotneed.com/</a>



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li>async pipe</li>
    <li>Unsubscribe</li>
    <li>Track By function</li>
    <li>Webpack Bundle Analyzer</li>
    <li>You (might) not need</li>
    <li class="animated fadeInUp tobuild">import *</li>
</ol>



<slide class="bg-black-blue" .dark">
## import *

import { chunk } from “lodash”<br>
vs.<br>
import * from “lodash”



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li>async pipe</li>
    <li>Unsubscribe</li>
    <li>Track By function</li>
    <li>Webpack Bundle Analyzer</li>
    <li>You (might) not need</li>
    <li>import *</li>
    <li class="animated fadeInUp tobuild">Global scss files vs. styles per component</li>
</ol>



<slide class="bg-black-blue" .dark">
## Styles per component

<ol>
<li class="animated fadeInUp tobuild">Properties will be loaded only if the component is used in the rendered page = <span style="color: green">better performance</span></li>
<li class="animated fadeInUp tobuild">The SCSS is scoped and simplified = <span style="color: green">better productivity</span></li>
<li class="animated fadeInUp tobuild">Styles per component overwrites global styles</li>
</ol>



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li>async pipe</li>
    <li>Unsubscribe</li>
    <li>Track By function</li>
    <li>Webpack Bundle Analyzer</li>
    <li>You (might) not need</li>
    <li>import *</li>
    <li>Global scss files vs. styles per component</li>
    <li class="animated fadeInUp tobuild">Dead-code elimination/Tree shaking</li>
</ol>



<slide class="bg-black-blue" .dark">
## Dead-code elimination/Tree shaking

<p class="tobuild">
When using<br>
`ng build --prod`<br>
to build, the angular CLI will compile and bundle all components into the application.<br><br>
</p>

<p class="tobuild">
When using<br>
`ng build --prod --build-optimizer`<br>
to build, all of the unused components will be omitted.<br>
`--build-optimizer` evokes tree shaking (term commonly used in the JavaScript context for dead-code elimination) on Webpack.<br><br>
</p>

<p class="tobuild">Unfortunately, this can cause some bugs.</p>



<slide class="bg-black-blue" .dark">
## Dead-code elimination/Tree shaking

<br>
#### Rather than excluding <span style="color: saddlebrown">dead code</span> <i style="color: saddlebrown" class="fa fa-leaf"></i><br> {.aligncenter}
#### we should including <strong style="color: green">live code</strong> <i style="color: green" class="fa fa-leaf"></i> {.aligncenter}


<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li>async pipe</li>
    <li>Unsubscribe</li>
    <li>Track By function</li>
    <li>Webpack Bundle Analyzer</li>
    <li>You (might) not need</li>
    <li>import *</li>
    <li>Global scss files vs. styles per component</li>
    <li>Dead-code elimination/Tree shaking</li>
    <li class="animated fadeInUp tobuild">One-time string initialization</li>
</ol>



<slide class="bg-black-blue" .dark">
## One-time string initialization
<br><br>
`[label]="'Save'"` vs `label="Save"`
<br><br>
<blockquote class="text-quote tobuild">
    <p>
    You should omit the brackets when all of the following are true:
    <ul>
        <li>The target property accepts a string value.</li>
        <li>The string is a fixed value that you can put directly into the template.</li>
        <li>This initial value never changes.</li>
    </ul>
        <cite><a href="https://angular.io/guide/template-syntax">angular.io</cite>
    </p>
</blockquote>



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li>async pipe</li>
    <li>Unsubscribe</li>
    <li>Track By function</li>
    <li>Webpack Bundle Analyzer</li>
    <li>You (might) not need</li>
    <li>import *</li>
    <li>Global scss files vs. styles per component</li>
    <li>Dead-code elimination/Tree shaking</li>
    <li>One-time string initialization</li>
    <li class="animated fadeInUp tobuild">Dependencies between components</li>
</ol>



<slide class="bg-black-blue" .dark">
## Dependencies between components


##### NGD: Angular Dependencies Graph
<a href="https://raw.githubusercontent.com/compodoc/ngd/master/screenshots/dependencies-4.png" target="_blank">
    <img class="aligncenter" src="https://raw.githubusercontent.com/compodoc/ngd/master/screenshots/dependencies-4.png">
</a>

<a href="https://camo.githubusercontent.com/9f1ae19a23609ef67f684a9e792d774232d5b471/68747470733a2f2f63646e2e7261776769742e636f6d2f636f6d706f646f632f6e67642f6d61737465722f73637265656e73686f74732f646570656e64656e636965732e6d6174657269616c322e737667" target="_blank">
    <img class="aligncenter" src="https://camo.githubusercontent.com/9f1ae19a23609ef67f684a9e792d774232d5b471/68747470733a2f2f63646e2e7261776769742e636f6d2f636f6d706f646f632f6e67642f6d61737465722f73637265656e73686f74732f646570656e64656e636965732e6d6174657269616c322e737667">
</a>



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li>async pipe</li>
    <li>Unsubscribe</li>
    <li>Track By function</li>
    <li>Webpack Bundle Analyzer</li>
    <li>You (might) not need</li>
    <li>import *</li>
    <li>Global scss files vs. styles per component</li>
    <li>Dead-code elimination/Tree shaking</li>
    <li>One-time string initialization</li>
    <li>Dependencies between components</li>
    <li class="animated fadeInUp tobuild">CSS vs. JS animations</li>
</ol>



<slide class="bg-black-blue" .dark">
## CSS vs. JS animations

<p class="text-cols">
    <span class="tobuild">
        CSS animations are ideal for smaller, self-contained states for UI elements,
        e.g. a sidebar with menu appearing from the side, a tooltip showing on hover. 
    </span>
    <br><br>
    <span class="tobuild">
        JavaScript gives more control over animations,
        e.g. possibility to stop, slow down, reverse or pause the animation.
    </span>
</p>



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li>async pipe</li>
    <li>Unsubscribe</li>
    <li>Track By function</li>
    <li>Webpack Bundle Analyzer</li>
    <li>You (might) not need</li>
    <li>import *</li>
    <li>Global scss files vs. styles per component</li>
    <li>Dead-code elimination/Tree shaking</li>
    <li>One-time string initialization</li>
    <li>Dependencies between components</li>
    <li>CSS vs. JS animations</li>
    <li class="animated fadeInUp tobuild">Lazy loading</li>
</ol>



<slide class="bg-black-blue" .dark">
## Lazy loading

Lazy loading loads only those modules and components that are needed. <br><br>
If the user is not an admin, there is no need to load the entire AdminModule. <br><br>
If the user is not signed in into the application and uses it only as an anonymous user, there is no need to load the AccountModule, which allows for view and edit the profile.



<slide class="bg-black-blue" .dark">
## Lazy loading

<p class="text-cols">
    <span class="tobuild">
        const routes: Routes = [<br>
            &nbsp;&nbsp;&nbsp;{<br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path: '',<br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;component: HomeComponent<br>
            &nbsp;&nbsp;&nbsp;},<br>
            &nbsp;&nbsp;&nbsp;{<br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path: 'login',<br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;component: LoginComponent<br>
            &nbsp;&nbsp;&nbsp;}<br>
        ];
    </span>
    <br><br>
    <span class="tobuild">
       const routes: Routes = [<br>
           &nbsp;&nbsp;&nbsp;{<br>
           &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path: '',<br>
           &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;component: HomeComponent<br>
           &nbsp;&nbsp;&nbsp;},<br>
           &nbsp;&nbsp;&nbsp;{<br>
           &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path: 'login',<br>
           &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;loadChildren: './login/login.module#LoginModule' <br>
           &nbsp;&nbsp;&nbsp;}<br>
       ];
    </span>
</p>



<slide class="bg-black-blue" .dark">
## What can we do?

<ol>
    <li>Code Minification</li>
    <li>OnPush Change Detection</li>
    <li>Pure pipes instead of functions/getters in templates</li>
    <li>async pipe</li>
    <li>Unsubscribe</li>
    <li>Track By function</li>
    <li>Webpack Bundle Analyzer</li>
    <li>You (might) not need</li>
    <li>import *</li>
    <li>Global scss files vs. styles per component</li>
    <li>Dead-code elimination/Tree shaking</li>
    <li>One-time string initialization</li>
    <li>Dependencies between components</li>
    <li>CSS vs. JS animations</li>
    <li>Lazy loading</li>
    <li class="animated fadeInUp tobuild">Throw it away to the backend</li>
</ol>


<slide class="bg-black-blue" .dark">
## The end