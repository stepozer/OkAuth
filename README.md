OkAuth
======

Auth class for www.odnoklassniki.ru

<h3>How to use<h3>

<ol>
	<li>First create aplication on odnoklassniki.ru</li>
	<li>Create action login by odnoklassniki.ru
<pre>def loginByOk
	@options = {
		'client_id'         => [your_app client_id],
		'scope'             => "VALUABLE ACCESS",
		'redirect_uri'      => [callback_action],
		'client_secret'     => [your_app_client_secret],
	}
	authByOk = OkAuth.new(@options)
	redirect_to authByOk.getAuthUrl
end</pre></li>
	<li>Create callback action
<pre>def loginByOkCallback
	get = request.GET
	@options = {
		'client_id'         => [your_app_client_id],
		'scope'             => "VALUABLE ACCESS",
		'redirect_uri'      => [callback_action],
		'client_secret'     => [your_app_client_secret],
		'application_key'   => [your_app_client_public],
	}
	authByOk = OkAuth.new(@options)
	userOkData = authByOk.getUserData(get["code"])
end</pre></li>
  <li>Save userdata in DB and login him</li>
</ol>
