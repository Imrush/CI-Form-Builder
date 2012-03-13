CI Form Builder
=================

I got tired of building the same forms over and over. I'm fairly new to CI and after building a few sites and creating the same form structure over and over again I decided to automate as much as possible.

I'm using Bootstrap 2, from Twitter as the markup framework.

Installation
------------

Add `Form_builder.php` to `/application/libraries`

Controller
----------

Call Form Builder from your controller by using `$this->load->library('form_builder');`

Form Builder requires an array of fields.

    $data['form'] = array(
        'attr' => array(
        'url' => 'my/submit',
            'class' => 'form-horizontal'
        ),
        'email' => array(
            'type' => 'input',
            'label' => 'Email',
            'attr' => array('placeholder' => 'youremail@example.com'),
        ),
        'password' => array(
            'type' => 'password',
            'label' => 'Password',
            'attr' => array('help_text' => 'Your password must be more than 6 characters, 0-9 a-z A-Z'),
        ),
        'actions' => array(
            'submit' => 'Submit the Form',
            'reset' => array(
                'label' => 'Reset',
                'class' => 'btn-inverse'
            )
        )
    );

Here is a more complex example:

    $data['form'] = array(
        'attr' => array(
            'url' => 'my/action',
            'class' => 'form-horizontal'
        ),
        'id' => array(
            'type' => 'hidden',
            'attr' => array('value' => '123456')
        ),
        'firstname' => array(
            'type' => 'input',
            'required' => TRUE,
            'label' => 'First Name',
            'attr' => array('placeholder' => 'Enter your First Name')
        ),
        'password' => array(
            'type' => 'password',
            'required' => TRUE,
            'label' => 'Password',
            'attr' => array('help_text' => 'This is a quick message to ensure you have all the help you need')
        ),
        'city' => array(
            'type' => 'select',
            'label' => 'City',
            'attr' => array(
                'value' => 'NC',
                'help_text' => 'Choose from the list above',
                'extra' => 'class="test"'
            ),
            'options' => array(
                'AR' => 'Arizona',
                'CA' => 'California',
                'NC' => 'North Carolina',
                'SC' => 'South Carolina',
            )   
        ),
        'message' => array(
            'type' => 'textarea',
            'required' => TRUE,
            'label' => 'Message',
            'attr' => array(
                'rows' => 5,
                'cols' => 30
            )
        ),
        'favoriteActor' => array(
            'type' => 'checkbox',
            'label' => 'Who is your favorite actor',
            'attr' => array('help_text' => 'This is helpful!'),
            'options' => array(
                'adamSandler' => array('label' => 'Adam Sandler'),
                'jimCarey' => array('label' => 'Jim Carey'),
                'michaelBluthe' => array('label' => 'Michael Bluthe')
            )
        ),
        'favoriteActorOnce' => array(
            'type' => 'radio',
            'label' => 'Who is your favorite actor (Choose One)',
            'attr' => array('help_text' => 'This is helpful!'),
            'options' => array(
                'adamSandler' => array('label' => 'Adam Sandler'),
                'jimCarey' => array('label' => 'Jim Carey'),
                'michaelBluthe' => array('label' => 'Michael Bluthe')
            )
        ),
        'actions' => array(
            'submit' => 'Submit the Form',
            'reset' => array(
                'label' => 'Reset',
                'class' => 'btn-inverse'
            )
        )
    );

The View
--------

From inside the view you call the `create_form()` method.

    <?php $this->form_builder->create_form($form); ?>