### Codeigniter adaptation ###

This is the same file as the one in server/php.php but slightly modified for use in codeigniter.

**Usage**
It is has been adapted for use as a codeigniter library<br/>
This function can be placed in a controller. It will be the one to receive the ajax calls from the client

```php
	function file_upload()
	{
		$sizeLimit = 10 * 1024 * 1024 ;
		$allowedExtensions = array("gif","jpg","png","bmp");
		$params = array('allowedExtensions'=>$allowedExtensions,'sizeLimit'=>$sizeLimit,"change_filename"=>false);
		$this->load->library('qqfileuploader',$params);
		$result = $this->qqfileuploader->handleUpload('./assets/images/uploads/');
		// to pass data through iframe you will need to encode all html tags
		echo htmlspecialchars(json_encode($result), ENT_NOQUOTES);		
	}
```