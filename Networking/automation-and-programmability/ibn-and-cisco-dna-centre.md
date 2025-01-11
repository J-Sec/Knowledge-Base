# IBN and Cisco DNA Centre

{% hint style="info" %}
<mark style="color:blue;">**Intent-based networking (IBN)**</mark> is a networking approach that uses automation and artificial intelligence to translate high-level business intents into network configurations and continuously ensures the network operates as intended.
{% endhint %}

{% hint style="info" %}
<mark style="color:blue;">**Cisco DNA Centre**</mark> is a centralised management platform that leverages automation, analytics, and AI to simplify the design, provisioning, and operation of enterprise networks.
{% endhint %}

## IBN

* Business objectives for the network are expressed as intent.&#x20;
* IBN captures business intent and uses analytics, machine learning, and automation to align the network continuously and dynamically as business needs change.
* IBN captures and translates business intent into network policies that can be automated and applied consistently across the network.
* Cisco views IBN as having three essential functions: translation, activation, and assurance. These functions interact with the underlying physical and virtual infrastructure

<figure><img src="../.gitbook/assets/Screenshot 2025-01-10 at 09.24.32.png" alt=""><figcaption></figcaption></figure>

* **Translation** - The translation function enables the network administrator to express the expected networking behaviour that will best support the business intent.
* **Activation** - The captured intent then needs to be interpreted into policies that can be applied across the network. The activation function installs these policies into the physical and virtual network infrastructure using network-wide automation.
* **Assurance** - In order to continuously check that the expressed intent is honoured by the network at any point in time, the assurance function maintains a continuous validation-and-verification loop.

### Network Infrastructure as Fabric

{% hint style="info" %}
A <mark style="color:blue;">**Fabric**</mark> in networking is an interconnected system of devices and switches that uses software-defined principles to enable seamless communication, automation, and policy enforcement across the network.
{% endhint %}

* Fabric is a term used to describe an overlay that represents the logical topology used to virtually connect to devices
* The underlay network is the physical topology that includes all hardware required to meet business objectives.

***

## Cisco DNA

* Cisco implements the IBN fabric using Cisco DNA
* The business intent is securely deployed into the network infrastructure (the fabric).&#x20;
* Cisco DNA then continuously gathers data from a multitude of sources (devices and applications) to provide a rich context of information.&#x20;
  * This information can then be analysed to make sure the network is performing securely at its optimal level and in accordance with business intent and network policies.
* Cisco DNA is a system that is constantly learning, adapting to support the business needs.

<figure><img src="../.gitbook/assets/Screenshot 2025-01-10 at 11.30.03.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2025-01-10 at 11.30.37.png" alt=""><figcaption></figcaption></figure>

