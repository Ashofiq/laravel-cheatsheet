# laravel-cheatsheet

Before proceeding to the cheat sheet, we will first briefly introduce you to what exactly Laravel is and its advantages.



### What is Laravel?

Laravel is a PHP web framework offering a comprehensive set of tools and resources useful for developing high-quality web applications. It follows the Model-View-Controller (MVC) architectural design pattern.
Created by Taylor Otwell, the Laravel framework is licensed under the MIT license.
It is packed with built-in features and a wide variety of compatible packages and extensions, making it one of the most popular PHP web frameworks.



### Advantages of Laravel

Here are some key advantages of using the Laravel framework.

The Laravel framework is easy to use, simple, and quick. As it is one of the most widely used PHP frameworks, many experienced developers are familiar with it and might have developed interactive web applications.

It offers advanced security features, enabling developers to protect their websites from cyber attacks. It uses a Bcrypt hashing algorithm, meaning that it does not save any password in the database.

Laravel supports out-of-the-box caching, which significantly enhances a website’s performance. Also, developers can effortlessly perform other speed optimization techniques, like database indexing and memory use reduction.
This framework has a built-in website that can efficiently handle the volume of traffic coming to a website. Therefore, it is also beneficial for traffic handling.
Using Laravel, developers can build fully-fledged and responsive eCommerce websites or B2B sites.
Laravel has clean APIs, making it easier to integrate your website with third-party applications.



### Laravel Doc

### Routes in Laravel

```
Route::get('func', function(){}); Route::get('func', 'ControllerName@function'); Route::controller('func', 'argController');
```

### RESTful Controllers

```
Route::resource('posts','PostsController');
```


### Specify a subset of actions to handle on the route

```
Route::resource('user', 'UserController',['only' = Route::resource('project', 'ProjectController',['e
```
### Triggering Errors

```
App::abort(404);
$handler->missing(...) in ErrorServiceProvider::bo throw new NotFoundHttpException;
```

### Route Parameters

```
Route::get('func/', function($arg){});
Route::get('func/', function($arg = 'arg'){});
```


### HTTP Verbs

```
Route::any('func', function(){});
Route::post('func', function(){});
Route::put('func', function(){});
Route::patch('func', function(){});
Route::delete('func', function(){});
```


#### RESTful actions

Route::resource('func', 'FuncController');
Registering A Route For Multiple Verbs
Route::match(['get', 'post'], '/', function(){});
### Secure Routes(TBD)
Route::get('func', array('https', function(){}));
### Route Constraints

Route::get('func/', function($arg){})
->where('arg', '[0-9]+'); Route::get('func//', function($arg, $arg2){})
->where(array('arg' => '[0-9]+', 'arg2' => '[A-Za-

### Set a pattern to be used across routes
```
Route::pattern('arg', '[0-9]+')
```

### HTTP Middleware
### Assigning Middleware To Routes
```
Route::get('/', function () {
        //
})->middleware(['auth', 'other']);

Route::group(['prefix' => 'admin',  'middleware' => 'auth'], function()
{
    //All the routes that belongs to the group goes here
    Route::get('dashboard', function() {} );
});

```

### Named Routes

```
Route::currentRouteName();
Route::get('func/arg', array('as' => 'args', function(){}));

Route::get('user/profile', [
'as' => 'profile', 'uses' => 'UserController@show
]);

Route::get('user/profile', [UserController::class, ‘show’])->name(‘profile’);

$url = route('profile');
$redirect = redirect()->route('profile');
```

### Route Prefixing
```
Route::group(['prefix' => 'admin'], function()
{
Route::get('users', function(){
return 'Matches The "/admin/users" URL';
});
});
```

### Route Namespacing

### This route group will carry the namespace ‘arg1\arg2’

```
Route::group(['prefix' => 'prefix','namespace'=>'Admin'], function () {
    // your routes with"App\Http\Controllers\Admin" Namespace
});

Route::namespace('Admin')->group(function () {
    // your routes with"App\Http\Controllers\Admin" Namespace
});
```

### Sub-Domain Routing

```
Route::domain('{account}.example.com')->group(function () {
    Route::get('user/{id}', function ($account, $id) {
        //
    });
});
```

### will be passed to the closure
```
Route::get('{foo}', array('name' => 'foo.home', 'uses' => function(){
    $fooController = $app->make('FooController');
    return $fooController->callAction('home', $parameters = array());
}));
```

### Laravel Redirect
```
return Redirect::to('arg1/arg2');
return Redirect::to('arg1/arg2')->with('key', 'val return Redirect::to('arg1/arg2')->withInput(Input: return Redirect::to('arg1/arg2')->withInput(Input: return Redirect::to('arg1/arg2')->withErrors($vali
```

### Redirect response to the previous location

return Redirect::back();

### Redirect response for the named routes
```
return Redirect::route('arg');
return Redirect::route('arg', array('value')); 
return Redirect::route('arg', array('key' => 'value'));
return redirect('/path');
```

### Laravel Cache
```
Cache::put('key', 'value', $minutes);
Cache::add('key', 'value', $minutes);
Cache::forever('key', 'value'); Cache::remember('key', $minutes, function(){ retur Cache::rememberForever('key', function(){ return ' Cache::forget('key');
Cache::has('key');
Cache::get('key'); Cache::get('key', 'default');
Cache::get('key', function(){ return 'default'; })
Cache::tags('my-tag')->put('key','value', $minutes
Cache::tags('my-tag')->has('key');
Cache::tags('my-tag')->get('key');
Cache::tags('my-tag')->forget('key');
Cache::tags('my-tag')->flush(); Cache::increment('key'); Cache::increment('key', $amount); Cache::decrement('key'); Cache::decrement('key', $amount); Cache::section('group')->put('key', $value);
Cache::section('group')->get('key');
Cache::section('group')->flush();
```

### Laravel Mail

```
Mail::send('email.view', $data, function($message) Mail::send(array('html.view', 'text.view'), $data, Mail::queue('email.view', $data, function($message Mail::queueOn('queue-name', 'email.view', $data, $ Mail::later(5, 'email.view', $data, function($mess
```

### Laravel Response

```
return Response::make($contents); return Response::make($contents, 200);
return Response::json(array('key' => 'value')); return Response::json(array('key' => 'value'))
->setCallback(Input::get('callback')); return Response::download($filepath);
return Response::download($filepath, $filename, $h
```


### Create a response and modify a header value

```
$response = Response::make($contents, 200);
$response->header('Content-Type', 'application/jso return $response;
```

### Attach a cookie to a response

```
return Response::make($content)
->withCookie(Cookie::make('key', 'value'));
```

### Laravel Log
* The logger provides the seven logging levels defined in RFC 5424: debug, info, notice, warning, error, critical, and alert.

```
Log::info('info'); 
Log::info('info',array('context'=>'additional info Log::error('error');
Log::warning('warning');
```

add listener


Log::listen(function($level, $message, $context) {


### Laravel Input

```
Input::get('key');
```

### Default if the key is missing

```
Input::get('key', 'default'); Input::has('key');
Input::all();
```

### Retrieve only ‘arg’ and ‘arg1’ when getting input

```
Input::only('arg', 'arg1');
```

### Discard ‘arg’ when getting input
```
Input::except('arg');
Input::flush();
```

### Laravel Environment

```
$environment = app()->environment();
$environment = App::environment();
$environment = $app->environment();
```

### The environment is local

```
if ($app->environment('local')){}
```
### The environment is either local OR staging…

```
if ($app->environment('local', 'staging')){
```

### Laravel Blade
### Show a section in a template

```
@yield('name') @extends('layout.name')
```

### Begin a section

```
@section('name')
```


### End a section

```
@stop
```
### End a section and yield

```
@section('sidearg1') @show
@parent @include('view.name')
@include('view.name', array('key' => 'value')); @lang('messages.name')
@choice('messages.name', 1); @if
@else @elseif @endif @unless @endunless @for @endfor @foreach @endforeach @while @endwhile
```


### forelse
```
@forelse($users as $user) @empty
@endforelse
```
### foreach
```
@foreach($users as $user) @empty
@endforeach
```

### Print content

```
{{ $var }}
```

### Print escaped content

```
{{{ $var }}}
```
### Print unescaped content
```
{!! $var !!}
{{-- Blade Comment --}}
```
### Printing Data After Checking For Existence

```
{{{ $name or 'Default' }}}
```
### Displaying Raw Text With Curly Braces

```
@{{ This will not be processed by Blade }}
```

### Laravel URL

```
URL::full();
URL::current();
URL::previous();
URL::to('arg/arg1', $parameters, $secure); URL::action('UserController@item', ['id'=>123]);
```

### need be inappropriate namespace

```
URL::action('Auth\AuthController@logout'); URL::action('argController@method', $parameters, $ URL::route('arg', $parameters, $absolute); URL::secure('arg1/arg2', $parameters); URL::asset('css/arg.css', $secure); URL::secureAsset('css/arg.css'); URL::isValidUrl('http://example.com'); URL::getRequest();
URL::setRequest($request);

```


### Laravel HTML

HTML::macro('name', function(){});

Convert an HTML string to entities

HTML::entities($value);

Convert entities to HTML characters

HTML::decode($value);

Generate a link to a JavaScript file

HTML::script($url, $attributes);

Generate an HTML image element

HTML::image($url, $alt, $attributes);

Generate a HTML link

HTML::link($url, 'title', $attributes, $secure);

Generate a HTTPS HTML link to an asset

HTML::linkSecureAsset($url, 'title', $attributes);

Generate a HTML link to a named route

HTML::linkRoute($name, 'title', $parameters, $attr

### Generate a HTML link to a controller action

```
HTML::linkAction($action, 'title', $parameters, $a
```

### Generate a HTML link to an email address

```
HTML::mailto($email, 'title', $attributes);
```

### Obfuscate an email address to prevent spam-bots from sniffing it
```
HTML::email($email);
```

### Soft Delete

```
Model::withTrashed()->where('users', 2)->get();
```
### Delete 
```
	User::first()->delete();
```

### Include the soft deleted models in the results

```
Model::withTrashed()->where('users', 2)->restore() Model::where('users', 2)->forceDelete();
```

### Force the result set to only include soft deletes

```
Model::onlyTrashed()->where('users', 2)->get();
```
### Restoring a soft deleted model is pretty easy too:
```
User::withTrashed()->where('id', 1)->restore();
```
### Events

```
Model::creating(function($model){}); Model::created(function($model){}); Model::updating(function($model){}); Model::updated(function($model){}); Model::saving(function($model){}); Model::saved(function($model){}); Model::deleting(function($model){}); Model::deleted(function($model){}); Model::observe(new argObserver);
```

### Laravel Joins
### The Join Statement

```
DB::table('users')
->join('contacts', 'users.id', '=', 'cont
->join('orders', 'users.id', '=', 'orders
->select('users.id', 'contacts.phone')->get();
```

### Left Join Statement

```
DB::table('users')
->leftJoin('posts', 'users.id', '=', 'posts.u
->get();

select * from users where name = 'Name' or (points and title <> 'Admin')

DB::table('users')
->where('name', '=', 'John')
->orWhere(function($query)
{
$query->where('votes', '>', 100)
->where('title', '<>', 'Admin')
})
->get();
```

### Laravel Aggregates
```
$users = DB::table('game')->count();
$price = DB::table('game')->max('points');
$price = DB::table('game')->min('points');
$price = DB::table('game')->avg('points');
$total = DB::table('game')->sum('points');
```
### Laravel Raw Expressions
```
DB::table('name')->remember(5)->get();
DB::table('name')->remember(5, 'cache-key-name')->get();
DB::table('name')->cacheTags('my-key')->remember(5)->get();
DB::table('name')->cacheTags(array('my-first-key','my-second-key'))->remember(5)->get()
```
### Return the rows
```
DB::select('SELECT * FROM users WHERE id = ?', arr
```
### Return affected rows
```
DB::insert('insert into arg set arg1=2'); DB::update('update arg set arg1=2'); DB::delete('delete from arg1');
```
### Return void
```
DB::statement('update arg set arg1=2');
```
###  raw expression inside a statement
```
DB::table('name')->select(DB::raw('count(*) as cou
```
### Laravel Inserts / Updates / Deletes / Unions / Pessimistic Locking
### Insert
```
DB::table('users')->insert(
['email' => 'email@host.com', 'votes' => 0]
);
$id = DB::table('users')->insertGetId( ['email' => 'email@host.com', 'votes' => 0]
);
DB::table('users')->insert([
['email' => 'email@host.com', 'votes' => 0], ['email' => 'email@host.com', 'votes' => 0]
]);
```
### Update
```
DB::table('users')
->where('id', 1)
->update(['votes' => 1]); DB::table('users')->increment('votes');
DB::table('users')->increment('votes', 5);
DB::table('users')->decrement('votes');
DB::table('users')->decrement('votes', 5);
DB::table('users')->increment('votes', 1, ['name'
```


### Delete

```
DB::table('users')->where('votes', '<', 100)->dele DB::table('users')->delete();
DB::table('users')->truncate();
```

### Union
```
$first = DB::table('users')->whereNull('first_name
$users = DB::table('users')->whereNull('last_name'
```
### Pessimistic Locking
```
DB::table('users')->where('votes', '>', 100)->shar
DB::table('users')->where('votes', '>', 100)->lock
```
### Laravel Eloquent 
	
### Where
```
$detail = Detail::where("id","!=",50)->get();
// Any of the following may be used as the second parameter (and use the third param for the value)
// =, <, >, <=, >=, <>, !=, LIKE, NOT LIKE, BETWEEN, ILIKE
 
$detail = Detail::where(function ($query) {
  $query->where('a', '=', 1)
      ->orWhere('b', '=', 1);
})->get();
 
$detail = Detail::whereRaw('age > ? and votes = 100', array(25))->get();
 
$detail = Detail::whereRaw(DB::raw("id in (select detail_id from students GROUP BY students.detail_id)"))->get();
 
$detail = Detail::whereExists(function($query){
  $query->select(DB::raw(1))
      ->from('students')
      ->whereRaw('students.detail_id = details.id')
      ->groupBy('students.detail_id')
      ->havingRaw("COUNT(*) > 0");
})->get();
// Any of the following may be used instead of Detail::whereExists
// ->orWhereExists(), ->whereNotExists(), ->orWhereNotExists()
 
$detail = Detail::whereIn('column',[1,2,3])->get();
// Any of the following may be used instead of Detail::whereExists
// ->orWhereIn(),
 
$detail = Detail::whereNotIn('id', function($query){
  $query->select('student_id')
  ->from('students')
  ->groupBy('students.student_id');
})->get();
 
// Any of the following may be used instead of Detail::whereExists
// ->whereNotIn(), ->orWhereNotIn
```

### Joins
```
$product = Product:where('id', $productId)    ->join('businesses','product.business_id','=','businesses.id')
    ->select('product.id','businesses.name')->first();
 
$product = Product:where('id', $productId)
    ->leftJoin('businesses','product.business_id', '=', 'businesses.id')->select('product.id','businesses.name')
->first();
 
$product = Product:where('id', $productId)
    ->join('businesses',function($join) use($cats) {
      $join->on('product.business_id', '=', 'businesses.id')
    ->on('product.id', '=', $cats, 'and', true);})->first();
```
### Eager Loading
```
->with('table1','table2')
->with(array('table1','table2','table1.nestedtable3'))
->with(array('posts' => function($query) use($name){
  $query->where('title', 'like', '%'.$name.'%')
    ->orderBy('created_at', 'desc');
}))
```
### Grouping
```
->groupBy('state_id','locality')
->havingRaw('count > 1 ')
->having('items.name','LIKE',"%$keyword%")
->orHavingRaw('brand LIKE ?',array("%$keyword%"))
```

### Offset & Limit
```
->take(10)
->limit(10)
->skip(10)
->offset(10)
->forPage($pageNo, $perPage)
```
### Order
```
->orderBy('id','DESC')
->orderBy(DB::raw('RAND()'))
->orderByRaw('type = ? , type = ? ', array('published','draft'))
->latest() // on 'created_at' column
->latest('column')
->oldest() // on 'created_at' column
->oldest('column')
```
### Create
```
->insert(array('email' => 'john@example.com', 'votes' => 0))
->insert(array(  
  array('email' => 'taylor@example.com', 'votes' => 0),
  array('email' => 'dayle@example.com', 'votes' => 0)
)) //batch insert
->insertGetId(array('email' => 'john@example.com', 'votes' => 0)) //insert and return id
```
### Update
```
->update(array('email' => 'john@example.com'))
->update(array('column' => DB::raw('NULL')))
->increment('column')
->decrement('column')
->touch() //update timestamp
```
### Delete

```
->delete()
->forceDelete() // when softdeletes enabled
->destroy($ids) // delete by array of primary keys
->roles()->detach() //delete from pivot table: associated by 'belongsToMany'
```
### Getters
```
->find($id)
->find($id, array('col1','col2'))
->findOrFail($id)
->findMany($ids, $columns)
->first(array('col1','col2'))
->firstOrFail()
->all()
->get()
->get(array('col1','col2')) 
->getFresh() // no caching
->getCached() // get cached result
->chunk(1000, function($rows){
  $rows->each(function($row){
 
  });
})
->lists('column') // numeric index
->lists('column','id') // 'id' column as index
->lists('column')->implode('column', ',') // comma separated values of a column
->pluck('column')  //Pluck a single column's value from the first result of a query.
->value('column')  //Get a single column's value from the first result of a query.
```
### Paginated results
```
->paginate(10)
->paginate(10, array('col1','col2'))
->simplePaginate(10)
->getPaginationCount() //get total no of records
```

### Aggregate

```
->count()
->count('column')
->count(DB::raw('distinct column'))
->max('rating')
->min('rating')
->sum('rating')
->avg('rating')
->aggregate('sum', array('rating')) // use of aggregate functions
```

### Laravel Validation
```
 $validated = $request->validate([
        'title' => 'required|unique:posts|max:255',
        'body' => 'required',
    ]);
    
$request->validate([
    'title' => 'required|unique:posts|max:255',
    'author.name' => 'required',
    'author.description' => 'required',
]);
```
### Laravel Rules

### accepted active_url after:YYYY-MM-DD before:YYYY-MM-DD alpha
```
alpha_dash alpha_num array between:1,10 confirmed date
date_format:YYYY-MM-DD different:fieldname digits:value digits_between:min,max boolean
email exists:table,column image in:arg,arg1,...
not_in:arg,arg1,... integer
numeric ip max:value min:value
mimes:jpeg,png regex:[0-9] required
required_if:field,value required_with:arg,arg1,... required_with_all:arg,arg1,... required_without:arg,arg1,... required_without_all:arg,arg1,... same:field
size:value timezone
unique:table,column,except,idColumn Url
```

### Laravel Config
```
Config::get('app.timezone');
get with Default value
Config::get('app.timezone', 'UTC');
```

### set Configuration
```
Config::set('database.default', 'sqlite');
```

### Laravel DB (Query Builder)
### Basic Database Usage
```
DB::connection('connection_name');
```
### Running A Select Query
```
$results = DB::select('select * from users where i
$results = DB::select('select * from users where i
```
### Running A General Statement
```
DB::statement('drop table users');
```
### Listening For Query Events
```
DB::listen(function($sql, $bindings, $time){ code_
```
### Database Transactions
```
DB::transaction(function()
{
DB::table('users')->update(['votes' => 1]);
DB::table('posts')->delete();
});
DB::beginTransaction(); DB::rollback();
DB::commit();
```
### Laravel Composer Command
```
composer create-project laravel/laravel folder_nam composer install
composer update
composer dump-autoload [--optimize] composer self-update
composer require [options] [--] [vender/packages].
```
### Laravel Messages
### These can be used on the $message instance passed into
```
Mail::send() or Mail::queue()
$message->from('email@xyz.com', 'Name');
$message->sender('email@xyz.com', 'Name');
$message->returnPath('email@xyz.com');
$message->to('email@xyz.com', 'Name');

$message->cc('email@xyz.com', 'Name');
$message->bcc('email@xyz.com', 'Name');
$message->replyTo('email@xyz.com', 'Name');
$message->subject('Congratulations');
$message->priority(2);
$message->attach('arg\arg1.txt', $options);
```

### This uses in-memory data as attachments
```
$message->attachData('arg1', 'Data Name', $options
```
### Embed a file in the message and get the CID
```
$message->embed('arg\arg1.txt');
$message->embedData('arg', 'Data Name', $options);
```
### Get the underlying Swift Message instance
```
$message->getSwiftMessage();
```
### Laravel Request
```
url: http://a.com/b/c

Request::url();

path: /a/b

Request::path();

getRequestUri: /a/b/?c=d

Request::getRequestUri();

Returns user’s IP

Request::getClientIp();

getUri: http://xyz.com/a/b/?c=d

Request::getUri();

getQueryString: c=d

Request::getQueryString();
```

### Get the port scheme of the request (e.g., 80, 443, etc.)
```
Request::getPort();
```
### Determine if the current request URI matches a pattern
```
Request::is('arg/*');
```
### Get a segment from the URI (1 based index)
```
Request::segment(1);
```
### Retrieve a header from the request
```
Request::header('Content-Type');
```
### Retrieve a server variable from the request
```
Request::server('PATH_INFO');
```
### Determine if the request is the result of an AJAX call
```
Request::ajax();
```
### Determine if the request is over HTTPS
```
Request::secure();
```
### Get the request method
```
Request::method();
```
### Checks if the request method is of the specified type
```
Request::isMethod('post');
```
### Get raw POST data
```
Request::instance()->getContent();
```
### Get requested response format
```
Request::format();
```
### true if HTTP Content-Type header contains */json
```
Request::isJson();
```
### true if HTTP Accept header is application/json
```
Request::wantsJson();
```
### Laravel Auth
### Laravel Authentication

### Determine if the current user is authenticated
```
Auth::check();
```
### Get the currently authenticated user
```
Auth::user();
```
### Get the ID of the currently authenticated user
```
Auth::id();
```
### Attempt to authenticate a user using the given credentials
```
Auth::attempt(array('email' => $email, 'password'
```
### ‘Remember me’ by passing true to Auth::attempt()
```
Auth::attempt($credentials, true);
```
### Log in for a single request
```
Auth::once($credentials);
```
### Log a user into the application
```
Auth::login(User::find(1));
```
### Log the given user ID into the application
```
Auth::loginUsingId(1);
```
### Log the user out of the application
```
Auth::logout();
```
### Validate a user’s credentials
```
Auth::basic('username');
```
### Attempt to authenticate using HTTP Basic Auth
```
Auth::validate($credentials);
```
### Perform a stateless HTTP Basic login attempt
```
Auth::onceBasic();
```
### Send a password reminder to a user
```
Password::remind($credentials, function($message,
```
### Laravel Authorization Define abilities
```
Gate::define('update-post', 'Class@method'); Gate::define('update-post', function ($user, $post
```
### Passing multiple argument
```
Gate::define('delete-comment', function ($user, $p
```
### Check abilities
```
Gate::denies('update-post', $post); Gate::allows('update-post', $post); Gate::check('update-post', $post);
```

### Specified a user for checking
```
Gate::forUser($user)->allows('update-post', $post)
```
### Through User model, using Authorizable trait
```
User::find(1)->can('update-post', $post); User::find(1)->cannot('update-post', $post);
```

### Intercepting Authorization Checks
```
Gate::before(function ($user, $ability) {}); Gate::after(function ($user, $ability) {});
```

### Checking in Blade template
```
@can('update-post', $post) 
@endcan
with else@can('update-post', $post) @else
@endcan
```
### Generate a Policy
```
php artisan make:policy PostPolicy
```

### policy helper function
```
policy($post)->update($user, $post)
```
### Controller Authorization
```
$this->authorize('update', $post);
```
* for $user

```
$this->authorizeForUser($user, 'update', $post).
```

### Pagination
```
Auto-Magic Pagination
Model::paginate(15); Model::where('cars', 2)->paginate(15);
“Next” and “Previous” only
Model::where('cars', 2)->simplePaginate(15);
```
### Manual Paginator
```
Paginator::make($items, $totalItems, $perPage);
```
Print page navigators in view

$variable->links();
