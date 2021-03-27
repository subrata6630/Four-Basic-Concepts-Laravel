# The Five Basic Concepts of Laravel

* Route
* Model
* View 
* Controller 


### Route:
ধারণত ইংরেজি শব্দ route যাকে অনেক সময় আমরা বাংলায় বলি রুট যার অর্থ দাঁড়ায় গন্তব্যস্থলে পৌঁছানোর রাস্তা। আর Laravel Application এ route হচ্ছে URL থেকে request গ্রহণ করে এবং application কে resource এর জন্য নির্দেশনা প্রদান করে। আরো সহজ ভাবে বলা যায় route হল আপনার অ্যাপ্লিকেশনের একটি request এর বিপরীতে কোন URL টি hit হবে? বা কোথায় থেকে কি response করবে তা নির্ধারণের একটি উপায়। Laravel 5.5 এ সব route গুলো routes ফোল্ডারে তৈরী করা থাকে। এর মধ্যে web application এর route সমূহ routes/web.php তে লিখা হয়। এবং API এর জন্য route সমূহ routes/api.php তে লিখা হয়। Laravel Framework এ route এর সবচেয়ে বড় সুবিধা হচ্ছে আপনি এক যায়গা থেকেই সমস্ত route কে নিয়ন্ত্রণ করতে পারবেন অর্থাৎ পরবর্তিতে route সম্পর্কিত যেকোনো ধরনের পরিবর্তন এখান থেকেই করতে পারবেন।

### Laravel Route এর প্রাথমিক ধারণা
Laravel Route লিখার আগে আপনাকে PHP Anonymous Function, Closure এবং PHP Class এর Static Method সম্পর্কে ধারণা থাকা দরকার, আমরা ধরে নিলাম আপনি এই গুলো জানেন। তো আসা যাক কিভাবে route দিয়ে URL Request গুলো Manage করতে পারি। ধরুন আমাদের Web Application এ তিনটি পেজ আছে , সেগুলো যথাক্রমে Home, About এবং Contact. এখন Web Application ব্যবহারকারী এই তিনটি পেজ এর মধ্যে যাকে request করবে শুধু সংশ্লিষ্ট পেজটি response করবে। অনেকটা নিচের URL এর মত:

* for Home page:
* http://localhost:8000/

* for About page:
* http://localhost:8000/about

* for Contact page:
* http://localhost:8000/contact

 এখন এই তিনটি URL Request এর জন্য আপনি Laravel এর routes/web.php ফাইল এ ঠিক নিচের মত করে লিখতে পারেন।
 
 ```php
 Route::get('/', function (){
    echo "<h2>This is Home Page</h2>;
});
Route::get('/about', function (){
    echo "<h2> This is About Page</h2>";
});
Route::get('/contact', function (){
    echo "<h2> This is Contact Page</h2>";
}); 
 
 ```
 
 ### নোট: অবশ্যই ” php artisan serve ” command দিয়ে server run রাখতে ভুলবেননা।

ব্যাখ্যা: উপরোক্ত উদাহরণে আমরা Route class এর get() মেথডকে call করেছি। Route Class এর get() মেথডটি দুইটি Argument গ্রহণ করে। প্রথম Argument হিসেবে URL Path অর্থাৎ যেই URL এ hit করবে সেটি, এবং দ্বিতীয় Argument হিসেবে একটি Anonymous Function সাথে closure থাকতে পারে। যেমনঃ উপরোক্ত উদাহরণে আমাদের Home URL এর জন্য প্রথম আর্গুমেন্ট হিসেবে শুধু forward slash ( / ) ব্যবহার করি , যার দ্বারা Laravel route রুট ডোমেইনকে নির্দেশ করে। একই ভাবে About URL এর জন্য forward slash সাথে about (/about) এবং Contact URL এর জন্য forward slash সাথে contact(/contact) লিখি। আর তিনটি URL এর জন্যই দ্বিতীয় Argument হিসেবে একটি Anonymous Function ব্যবহার করি যার দ্বারা action কি হবে তা নির্ধারণ করি।

### Laravel Route এবং URL Parameter নিয়ে কাজ
অবশ্যই, কখনও কখনও আপনাকে আপনার route মধ্যে URI এর segment গুলিকে receive বা capture করতে হবে। এটি করার জন্য Laravel Route এ দুটি উপায় আছে যার মাধ্যমে আপনি URL- এর মাধ্যমে পাঠানো Parameter গুলিকে Capture করতে পারেন।

* Required Parameters
* Optional Parameters

