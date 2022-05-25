# Configure app service plans
An App Service plan defines a *set of compute resources for a web app* to run. 1+  can be configured to run 
on the same computing resources. Definition:
- Region
- \# of VM instances
- Size of VM instances

## How it works?
Free & Shared tiers, it receives CPU minutes on a shared VM instance and cannot scale out. An app in App
Service it is put into a *App Service plan*. All apps in the same plan share the same VM instances. Take in 
account that could put multiple apps in a plan and save costs. But, you can overload an plan and cause a 
downtime. Isolate app into a new plan when:
- It is resource-intesive
- You want to scale the app independently
- The app needs a resources in a different geographical region

## Pricing
- **Free & Shared**: many apps (even from other customers) run on the same VM. No SLA. Dev/Test. Metered on a 
per App basis.
- **Basic**: lower traffic requirements, not advanced autoscale. Pricing on size and # of instances. With 
Linux, supports Web App for Containers. Automatic Load balancing.
- **Standard**: running production workloads. Similar to basic but has autoscale.
- **Premium**: faster processors, SSDs, double memory-to-core ratio compared to Std. Higher scale via 
increased instance count. Enhanced perfomance.
- **Isolated**: mission critical workloads. Private, dedicated environment using Dv2-series VM with faster
processors, SSD, double memory-to-core ratio compared to Std. The env is called App Service Environment. 
Up to 100 instances.

## Types of scaling
**Scale up**: get more resources. You need to change the tier of the plan:
**Scale out**: get more instances

## Configure scaling
You specify the min/max instances and the set of rules.
Autoscale settings triggers:
- **Metric-based**: on application load.
- **Time-based**: scale when you see time patterns in your load.

## To consider
- Even if you have null load, you will have a minimum count of instances
- Have an adequate margin between the limits
- Have both scale-in and scale-out rule combination
- Choose the appropiate statistic for your metric
- Have a default count when metrics fails
- Configure autoscale notifications