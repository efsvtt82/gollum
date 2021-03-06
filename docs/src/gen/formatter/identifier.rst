.. Autogenerated by Gollum RST generator (docs/generator/*.go)

Identifier
==========

This formatter generates a (mostly) unique 64 bit identifier number from
the message payload, timestamp and/or sequence number. The number is be
converted to a human readable form.




Parameters
----------

**Generator**

  Defines which algorithm to use when generating the identifier.
  This my be one of the following values.
  By default this parameter is set to "time"
  
  

  **hash**

    The message payload will be hashed using fnv1a and returned as hex.
    
    

  **time**

    The id will be formatted YYMMDDHHmmSSxxxxxxx where x denotes the
    current sequence number modulo 10000000. I.e. 10.000.000 messages per second
    are possible before a collision occurs.
    
    

  **seq**

    The sequence number will be used.
    
    

  **seqhex**

    The hex encoded sequence number will be used.
    
    

Parameters (from core.SimpleFormatter)
--------------------------------------

**Source**

  This value chooses the part of the message the data to be formatted
  should be read from. Use "" to target the message payload; other values
  specify the name of a metadata field to target.
  By default this parameter is set to "".
  
  

**Target**

  This value chooses the part of the message the formatted data
  should be stored to. Use "" to target the message payload; other values
  specify the name of a metadata field to target.
  By default this parameter is set to "".
  
  

**ApplyTo**

  Use this to set Source and Target to the same value. This setting
  will be ignored if either Source or Target is set to something else but "".
  By default this parameter is set to "".
  
  

**SkipIfEmpty**

  When set to true, this formatter will not be applied to data
  that is empty or - in case of metadata - not existing.
  By default this parameter is set to false
  
  

Examples
--------

This example will generate a payload checksum and store it to a metadata
field called "checksum".

.. code-block:: yaml

	 ExampleConsumer:
	   Type: consumer.Console
	   Streams: console
	   Modulators:
	     - formatter.Identifier
	       Generator: hash
	       Target: checksum





