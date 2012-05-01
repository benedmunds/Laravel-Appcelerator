#Appcelerator ACS API bundle for Laravel  
A Laravel bundle that is a simple port of the Appcelerator ACS Javascript SDK to PHP  


##Setup
Install the bundle  

	$ php artisan bundle:install appcelerator

Include it in application/bundles.php  

	return array('appcelerator');


##Usage
In your routes.php simply start the bundle, set your login info, and call the API  
  
	Route::get('appcelerator/statuses', function()
	{
		$app_key  = '123';
		$email    = 'ben.edmunds@gmail.com';
		$password = '12345678';

		Bundle::start('appcelerator');

		$data = array(
			'where' => json_encode(array('user_id' => '4f9eb57a0020440def0056d3')),	
		);

		$output = Appcelerator\Appcelerator::init($app_key, $email, $password)
		                                     ->send_request('statuses/query.json', 'GET', $data);

		print_r($output);
		exit;
	});


	Route::get('appcelerator/create_status', function()
	{
		$app_key  = '123';
		$email    = 'ben.edmunds@gmail.com';
		$password = '12345678';
		
		Bundle::start('appcelerator');

		$data = array(
			'message' => 'api test message',	
		);

		$output = Appcelerator\Appcelerator::init($app_key, $email, $password)
		                                     ->send_request('statuses/create.json', 'POST', $data);
			
		print_r($output);
		exit;
	});


See [the Appcelerator documentation](http://cloud.appcelerator.com/docs/api/v1/statuses/info) for API details.

Bundle created by [Ben Edmunds](http://benedmunds.com) and [Shealan Foreshaw](http://twitter.com/#!/shealan) for [Swipe & Tap](http://twitter.com/#!/swipeandtap).