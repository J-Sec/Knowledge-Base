# Structured Troubleshooting Methods

There are several structured troubleshooting approaches that can be used. Which one to use will depend on the situation. Each approach has its advantages and disadvantages

## Bottom-Up

* Start with the physical layer and the physical components of the network and move up through the layers of the OSI model until the cause of the problem is identified.
* Bottom-up troubleshooting is a good approach to use when the problem is suspected to be a physical one.
* Most networking problems reside at the lower levels, so implementing the bottom-up approach is often effective.
* The disadvantage with the bottom-up troubleshooting approach is it requires that you check every device and interface on the network until the possible cause of the problem is found.
* Each conclusion and possibility must be documented so there can be a lot of paper work associated with this approach.&#x20;
* A further challenge is to determine which devices to start examining first.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-12-20 at 13.20.12.png" alt=""><figcaption><p>Bottom-Up Approach</p></figcaption></figure>

## Top-Down

* Starts with the end-user applications and moves down through the layers of the OSI model until the cause of the problem has been identified.
* End-user applications of an end system are tested before tackling the more specific networking pieces.&#x20;
* Use this approach for simpler problems, or when you think the problem is with a piece of software.
* The disadvantage with the top-down approach is it requires checking every network application until the possible cause of the problem is found.&#x20;
* Each conclusion and possibility must be documented.&#x20;
* The challenge is to determine which application to start examining first.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-12-20 at 13.21.20.png" alt=""><figcaption><p>Top-Down Approach</p></figcaption></figure>

## Divide-and-Conquer

* Select a layer and tests in both directions from that layer.
* Start by collecting user experiences of the problem, document the symptoms and then, using that information, make an informed guess as to which OSI layer to start your investigation
* When a layer is verified to be functioning properly, it can be assumed that the layers below it are functioning

<figure><img src="../../../.gitbook/assets/Screenshot 2024-12-20 at 13.32.51.png" alt=""><figcaption><p>Divide-and-Conquer Approach</p></figcaption></figure>

## Follow-the-Path

* Most basic troubleshooting technique.
* The approach first discovers the traffic path all the way from source to destination.
* The scope of troubleshooting is reduced to just the links and devices that are in the forwarding path.&#x20;
* The objective is to eliminate the links and devices that are irrelevant to the troubleshooting task at hand.&#x20;
* This approach usually complements one of the other approaches.

## Substitution

* Also called swap-the-component because you physically swap the problematic device with a known, working one
* If the problem is fixed, then the problem is with the removed device. If the problem remains, then the cause may be elsewhere.
* In specific situations, this can be an ideal method for quick problem resolution, such as with a critical single point of failure
* If the problem lies within multiple devices, it may not be possible to correctly isolate the problem.

## Comparison

* Also called the spot-the-differences approach and attempts to resolve the problem by changing the nonoperational elements to be consistent with the working ones
* Compare configurations, software versions, hardware, or other device properties, links, or processes between working and nonworking situations and spot significant differences between them
* The weakness of this method is that it might lead to a working solution, without clearly revealing the root cause of the problem.



## Guidelines for Selecting a Troubleshooting Method

To quickly resolve network problems, take the time to select the most effective network troubleshooting method.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-12-20 at 13.49.26.png" alt=""><figcaption></figcaption></figure>

