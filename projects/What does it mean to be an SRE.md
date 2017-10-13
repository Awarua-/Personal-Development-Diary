25/08/17

Started by reading the book Site Reliability Engineering, How Google runs production systems.

Key takeaways
Learn't about the different systems at a high level used at Google, of particular interest is Borg, a distributed cluster system. Its predessor is Kubernetes, I should look into this technology further.

Managed to get through the preface of the book and chapter one and two, which talks about what SRE is and how SRE works at Google and Google's systems.

01/09/17

SRE Book chapter 3, managing risk

Well I didn't actually write anything after reading the chapter last time. But from memory the key take aways where.
Have a reliability budget say 99.9% uptime means that you have 0.01% of the time the service can be unavailable to users.
In a year that works out to be 8.76 hours.

When defining the availability target you should also consider the error rate of other services beyond your control, for example wifi on celluar connection may have an error rate of 1% over your error budget of 0.1%. So in some cases will the user notice if a request to a service fails, they'll probably first blame their wireless connection or the internet in general.

You can never have 100% reliability the closer you try to get the cost will increase exponentially

The error budget allows for a dialogue between developers and SRE as if the available budget is still high then the development team can push out more releases.

06/10/17

SRE Book chapter 4, Service Level

Service Level Indicator (SLI): These are direct metrics or calculated metrics for reporting things like availability (Amount of time the service was down / up), request error rate, etc. And is traditionally displayed as a percentage, average, rate.

Service Level Objective (SLO): Are targets for SLI's like the latency for a request should be under the given SLI.
Publishing these SLO's is useful as it means that users don't get a false sense of the reliability of the service. It also helps with implementation as service owners can know what is important to work on or to consider during design or implementation.

Interesting article on Chubby, Chubby was too reliable which lead others to depend on it, so when it did happen to go down people would get mad. Chubby frequently exceeded its SLO's, so in response to this SRE team would perform syntetic outages of Chubby, so that service owners would learn to not rely on it too much.

Service Level Agreement (SLA): Usually contractual between the company and end user, usually has SLO's in it. There are also repercussions, financial reputation or otherwise for not meeting SLO's
