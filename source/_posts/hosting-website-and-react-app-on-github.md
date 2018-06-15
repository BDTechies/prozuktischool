---
title: গিট ও গিটহাব -  গিটহাব-এ (স্ট্যাটিক) ওয়েবসাইট হোস্ট
date: 2018-04-05 09:39:48
author: শহীদুল ইসলাম মজুমদার
tags:
- ওয়েব ডেভেলপমেন্ট
- html
- reactjs
- github
category: ওয়েব ডেভেলপমেন্ট
---
আমার মতো যারা HTML, CSS, JavaScript কিংবা ReactJS শিখছেন, হয়তো দুয়েকটি প্রজেক্টও করেছেন; কিন্তু টাকা কিংবা ডলারের অভাব অথবা না জানার কারণে হোস্ট করতে পারছেন না - তাদের জন্যই আমার আজকের লেখা। এই টিউটোরিয়ালটিতে আমরা দেখার চেষ্টা করবো কীভাবে গিটহাব ব্যবহার করে যেকোনো স্ট্যাটিক ওয়েবসাইট অর্থাৎ HTML, CSS ও JavaScript এ বানানো সাইট এমনকি ReactJS অ্যাপও হোস্ট করা যায়।

যা কিছু আপনার (ইন্সটল থাকা) লাগবে:

- Git ও Git ব্যবহারের বেসিক ধারণা
- GitHub অ্যাকাউন্ট
- NodeJS (React অ্যাপ হোস্ট করার জন্য)

### সাধারণ স্ট্যাটিক সাইট হোস্ট করা

আপনার যদি গিটহাব অ্যাকাউন্ট থাকে তবে লগইন করুন, আর না থাকলে একটি নতুন একাউন্ট তৈরি করে নিন। তারপর গিটহাব সাইটের মেন্যুতে থাকা <span class="highlight-text">+</span> চিহ্নতে ক্লিক করে একটি নতুন রিপোজিটরি বানিয়ে নিন। রিপোজিটরিটি আপনার কম্পিউটারে ডাউনলোড বা ক্লোন করে নিন। এবার কমান্ড লাইনের এইমাত্র ক্লোন করা ফোল্ডারটিতে যান। <span class="highlight-text">git status</span> কমান্ডটির মাধ্যমে সবকিছু ঠিক আছে কিনা চেক করুন।

এবার <span class="highlight-text">gh-pages</span> নামে নতুন একটি ব্রাঞ্চ তৈরি করার জন্য নিচের কমান্ডটি রান করান ($ সাইন কমান্ডের অংশ না):

<pre><code class="language-bash">$ git checkout -b gh-pages</code></pre>

ব্রাঞ্চ তৈরি হয়ে গেলে আপনার বানানো সাইটের দরকারি সব ফাইল কপি করে গিট থেকে ক্লোন করা ফোল্ডারটতে পেস্ট করুন। <span class="highlight-text">index.html</span> ফাইলটি যেনো গিট ফোল্ডারটির ভেতরেই থাকে। তারপর নিচের কমান্ডগুলো একে একে রান করান:

<pre><code class="language-bash">$ git add .
$ git commit -m "Added site to GitHub pages"
$ git push origin gh-pages</code></pre>

বিশ্বাস করুন আর নাইবা করুন। আপনার সাইট কিন্তু লাইভ অর্থাৎ দুনিয়াবাসীর দেখার জন্য উন্মুক্ত। সাইটের লিংকটি পেতে আপনার গিটহাব রিপোজিটরিটি ব্রাউজারে ওপেন করে তার সেটিংস অপশানটিতে ক্লিক করুন কিংবা নিচের ঠিকানাটি আপনার উপযুক্ত করে বদলিয়ে ব্রাউজারে ওপেন করুন।

<pre><code class="language-javascript">https://username.github.io/repo-name</code></pre>


এখানে <span class="highlight-text">username</span> এর জায়গায় আপনার গিটহাব ইউজারনেইম এবং <span class="highlight-text">repo-name</span> এর জায়গায় আপনার রিপোজিটরিটির নাম দিন।

### ReactJS সাইট হোস্ট করা
ReactJS হোস্ট করার জন্যও গিটহাবের একটি রিপোজিটরি এবং আপনার কম্পিউটারে তা ক্লোন করা থাকতে হবে। এবার আপনার প্রিয় কোড এডিটরে রিয়েক্ট প্রজেক্টটি ওপেন করুন। প্রজেক্টের <span class="highlight-text">package.json</span> ফাইলের <span class="highlight-text">scripts</span> অংশে নিচের লাইন দুটি যোগ করুন:

<pre><code class="language-bash">"predeploy": "npm run build",
"deploy": "gh-pages -d build"</code></pre>

একই ফাইলের শেষ <span class="highlight-text">}</span>-টির আগে নিচের লাইনটি যোগ করুন:

<pre><code class="language-json">"homepage": "http://username.github.io/repo-name"</code></pre>

<span class="highlight-text">package.json</span> ফাইলটি অনেকটা এরকম দেখাবে:

<pre><code class="language-json">{
  "name": "my-awesome-website",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "react": "^16.3.0",
    "react-dom": "^16.3.0",
    "react-scripts": "1.1.1"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"
  },
  "homepage": "http://sh4hids.github.io/my-awesome-website"
}</code></pre>

এবার গিটহাব থেকে ক্লোন করা ফোল্ডারটিতে আপনার রিয়েক্ট প্রজেক্টের `README.md` ছাড়া বাকি সবগুলো ফাইল কপি করে পেস্ট করুন। পেস্ট করা হলে কমান্ড লাইন থেকে ফোল্ডারটিতে যান এবং নিচের কমান্ডগুলো একে একে রান করান:

<pre><code class="language-bash">$ npm install
$ npm install -D gh-pages
$ npm run deploy</code></pre>

সবকিছু ঠিক থাকলে সাইটটি হোস্ট হয়ে যাওয়ার কথা। সাইটটিতে ভিজিট করার জন্য উপরে দেখানো পদ্ধতি অনুসরণ করুন। নির্দেশনাগুলোর মধ্যে কোনোটি বুঝতে অসুবিধা হলে মন্তব্যের ঘরে জানাতে পারেন। ইনশা আল্লাহ সর্বাত্মক সাহায্যের চেষ্টা করবো।