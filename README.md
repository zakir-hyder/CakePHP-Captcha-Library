CakePHP Captcha Library
==========================

CakePHP 2.1 :Put the "captcha" folder on path-to-cakephp-2.0/vendors/ on root vendors folder. Use following

    App::import('Vendor', 'captcha/captcha');

Since CakePHP 2.1 the Pages Controller is no longer part of the core but ships in the app folder. So my advice would be create UsersController and put the captcha_image() on that controller and and use the function on view
    
    $this->Html->url('/users/captcha_image');.

CakePHP 2.0 :Put the "captcha" folder on path-to-cakephp-2.0/app/vendors/ on App's vendors folder. Use following

    App::import('Vendor', 'captcha/captcha');

CakePHP 1.3 :Put the "captcha" folder on path-to-cakephp-1.3/vendors/ on the root vendors folder.

    App::import('Vendor', 'captcha/captcha');

CakePHP 1.2 :This post and code is for CakePHP 1.2 and CakePHP 1.3. For CakePHP 1.3 put the "captcha" folder on path-to-cakephp-1.3/vendors/ on the root vendors folder.

Now we implement it on our site. to do that we have to add a function the controller or we can add it to our pages controller.

    function captcha_image(){
    	App::import('Vendor', 'captcha/captcha');
    	$captcha = new captcha();
    	$captcha->show_captcha();
    }

Then we call it in our view.

    <img id="captcha" src="<?php echo $this->Html->url('/pages/captcha_image');?>" alt="" />

Add the following code to add refresh button

    <a href="javascript:void(0);" onclick="javascript:document.images.captcha.src="
    <?php echo $this->Html->url("/pages/captcha_image");?>?" + Math.round(Math.random(0)*1000)+1" >Reset</a>
To check the captcha in controller we will use this one.

    if($this->data['ContactMsge']['captcha']!=$this->Session->read('captcha'))
    {
    $this->Session->setFlash(__('Please enter correct captcha code and try again.', true));
    }

So as you can see you add this to you site very easily and it is very much customizable.

## Contact

Follow [@jambura.blog](https://www.facebook.com/jambura.blog) on Facebook 

### Creators

[Zakir Hyder](https://github.com/zakir-hyder)  
[@jambura.blog](https://www.facebook.com/jambura.blog)

## License

CakePHP Captcha Library is available under the MIT license. See the LICENSE file for more info.
