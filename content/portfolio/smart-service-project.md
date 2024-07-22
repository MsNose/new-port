---
title: Smart Service Project
date: 2023-12-13T12:49:27.000+06:00
thumbnail: images/portfolio/smart.png
service: Dashboard 
client: Goederenhub Maastricht
shortDescription: The Smart Service Project aimed to facilitate the green transition in the electric vehicle market. Our team has chosen  Urban Consolidation Centers (UCCs) as stakeholders, focusing especially on Goederenhub in Maastricht.
challenge: As municipalities move towards zero-emission zones by 2025 and stricter regulations by 2030, UCCs need to estimate their future needs for electric vans to comply with new environmental laws. The main challenge was to predict the logistic demand within Maastricht accurately and help UCCs prepare for this transition, despite their lack of resources and expertise in this area.
solution: Our team developed a dashboard with KPIs to support the green transition of UCCs in Maastricht. Using predictive models and survey data, we estimated logistic demand and calculated the number of trucks and energy consumption needed. The dashboard provides personalized predictions and scenarios, helping UCCs plan for the number of electric vans required and future energy and cost management.

---

{{< bootstrap_button link="https://github.com/MsNose/smart-service-project" alignment="vertical" >}}Look at the Project on Github!{{< /bootstrap_button >}}

---
  


{{< linkedin >}}



Throughout the project we leveraged the powerful capabilities of **Python**, **RStudio** and **Tableau**.

The project includes the following steps:

1. A model is trained that predicts the number of businesses per Maastricht region per business type.  
2. Survey data is used to determine the average number of pallets delivered per business type in Maastricht.
3. These values are used to determine the total logistic demand (in pallets) of Maastricht.
4. This information is then exported to be used by our dashboard that will make further calculations (number of trucks required, amount of electricity etc.)



## The situation

In the Netherlands, some municipalities signed up to be zero emission zones by 2025. This means, that from 2025 onwards, in these municipalities fuel based cars will face restrictions, and only the ones that are emitting considerably less are going to be let inside the city. This regulation is going to be even stricter in 2030, when only EVs will be allowed to enter. There are many areas that are going to be impacted by these changes, and one of them are UCCs.   
These logistic facilities function as connectors between the suppliers and the end-users. The large trucks drop their products at the UCCs, usually located at the border of the city, and then the smaller vans of UCCs distribute the products inside the city. Hence, their operation is within city borders where the new environmental regulations will be imposed. That is why UCCs need to start thinking about the green transition of their services. However, as we noticed, they don't have the knowledge and resources for appropiate estimations. That is why our team jumped in, and offered a solution. 

![](/images/portfolio/ucc.gif)


The goal was simple. Just help the UCC decide how many electric vans they will need. But this depends on a lot of things. Our team followed a logistic demand approach, where we predicted the number of vans based on the logistic demand in Maastricht. But how exactly did we do that?

## The data

So, basically we had two data sources to start: on one hand, the number of stores per sector per district in Maastricht, and on the other a self-conducted survey about store deliveries. Let's see why these things are relevant for calculating logistic demand.

### Number of businesses

The main client of UCCs are businesses. They don't deliver to customers directly. There are already specific companies like DHL or the national postal service who are taking care of that. Hence, to estimate how many electric vans the UCC needs, we have to know how many potential businesses can be targeted as clients in the upcoming years. These vary widely according to the type of activities and the location of the business, that is why we took the sector and the district into account. Thus, based on historical data from the past 10 years, we predicted the number of businesses in the upcoming years. To do this, we used the *compare_models* function from the *pycaret* package, which assigned to each business type a best fit model. 


### Delivery survey

While data about the number of business was available, the number of deliveries is not recorded in public datbases. Therefore, out team took the initiative, and created a quick survey about the deliveries in Maastricht. The survey included the following questions:  

  1. How often do you order deliveries?
  2. What is the range of each delivery expressed in EUR palettes?
  3. Who is your supplier?

To make the decision easier, we already included the potential answers  and ask the respondents to choose. Thus, with this user-friendly survey, we manage to contact around 80 businesses in Maastricht, covering all business types in all districts. Now, we had an idea about the volume and frequency of the total demand for UCC services. 

### Combining the 2 datasets

The real magic happens when we combine these two datasets. If we simply multiply the number of predicted businesses in a sector with the average number of pallets delivered per business type, then these values represent to total logistic demand in pallets in Maastricht. These values are the base for the further scenario calculations and market share targets fro the dashboard.


## The dashboard

It is hard to grab the true insights of the data analytics results by just looking at numbers. Especially, when so many different factors need to be considered, the UCC needs to be able to personalize the predictions according to its needs and preferences. So, we created 3 scenarios with Monte Carlo simulation, a good, and average and a bad one. 



{{< bootstrap_button link="/images/portfolio/Presentation.pdf" alignment="horizontal" >}}Presentation{{< /bootstrap_button >}}




 
{{< video "/images/portfolio/Screen Recording 2023-06-28 at 13.28.29.mp4" "my-5" >}}


