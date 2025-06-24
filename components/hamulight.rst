Hamulight RF
==========

.. seo::
    :description: Instructions for setting up the Hamulight RF component in ESPHome to control Hamulight's LED driver.
    :image: remote.svg
    :keywords: RF, Remote, TX, 433, Hamulight, light, led

The ``hamulight`` component will enable ESPHome to transmit RF remote signals for controlling Hamulight LED drivers
with ESP32 (S2/S3/C3) using the integrated RMT peripheral for precise RF signal generation.
An 433MHz RF transmitter needs to be hooked up.
This project is in no way associated, supported or otherwise linked to Hamulight B.V. or any of its affiliates!

This ESPHome custom component enables direct control of Hamulight RF-based lighting systems using an ESP32 (including
S2/S3/C3 and other variants). It replays the proprietary Hamulight RF protocol using the ESP32's RMT peripheral for
precise waveform generation. You can toggle lights on/off, pair with drivers (= max brightness button on the remote),
set brightness — all from Home Assistant. This component also includes an optional "command scan" feature which allows
to batch-send commands within a defined range for finding unknown commands (not populated on your remote).

The ESPHome Hamulight componenent is written as dynamical as possible to allow other devs to use it for other protocol
implementations as well.

ESPHome Hamulight does **not** use HomeAssistant's light entities. Reason for that is that this project is following a
stateless approach (as you never know, if a RF signal has been received and executed by the LED driver). This makes the
YAML configuration part a little bit more complex, but also more flexible at the same time.


How the Hamulight RF Protocol Works
-----------------------------------
**Protocol Summary**

xxx

.. code-block:: yaml

    # Example configuration entry
    status_led:
      pin: GPIOXX

.. note::

    If your device has a single LED that needs to be shared use  :doc:`status_led light platform </components/light/status_led>` instead.

Configuration variables:
------------------------

- **pin** (**Required**, :ref:`Pin Schema <config-pin_schema>`): The
  GPIO pin to operate the status LED on.
- **id** (*Optional*, :ref:`config-id`): Manually specify the ID used for code generation.

.. note::

    If your LED is in an active-LOW mode (when it's on if the output is enabled), use the
    ``inverted`` option of the :ref:`Pin Schema <config-pin_schema>`:

    .. code-block:: yaml

        status_led:
          pin:
            number: GPIOXX
            inverted: true

See Also
--------

- :ghedit:`Edit`
