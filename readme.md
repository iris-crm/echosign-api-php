#Adobe EchoSign PHP API

This PHP library wraps Adobe's EchoSign API, currently at Version 22. The library closely follows the documentation at https://secure.echosign.com/public/docs/EchoSignDocumentService22

##Requirements

* PHP 5.3
* SOAP module

##Version 1.1.0
This is currently a development library, not fully tested for production use

##Instalation

    composer require danielsan/echosign-api-php
    Please provide a version constraint for the danielsan/echosign-api-php requirement: 1.1.0

 Don't forget to include vendor/autoload.php to use it

##Usage

There are basic examples of all generally accessible methods in the examples folder. The EchoSign API has several methods that are only accessible by requesting special permission from the provider. Those methods are implemented in the wrapper, but examples are not provided.

###Simple Document Send

    $client = new SoapClient(EchoSign\API::getWSDL());
    $api = new EchoSign\API($client, 'YOUR API KEY');
    
    $file = EchoSign\Info\FileInfo::createFromFile('demo.pdf');
    
    $document = new EchoSign\Info\DocumentCreationInfo('Test sendDocument', $file);
    
    $recipients = new EchoSign\Info\RecipientInfo;
    $recipients->addRecipient($recipient_email);
    
    $document->setRecipients($recipients);
    
    $result = $api->sendDocument($document);
    
###Simple Embedded Widget Creation

    $client = new SoapClient(EchoSign\API::getWSDL());
    $api = new EchoSign\API($client, 'YOUR API KEY');

    $file = EchoSign\Info\FileInfo::createFromFile('demo.pdf');
    
    $widget = new EchoSign\Info\WidgetCreationInfo('Test createEmbeddedWidget', $file);
    
    $result = $api->createEmbeddedWidget($widget);
