# demography-inference

This is a short guide on the steps that you should follow to infer demography from SNP data. 

**1. Your data**
You have a **VCF** file obtained from a sequencing project. Here we assume that you have polymorphic data for 61 diploid individuals (Africans from the Yoruba population). 

**2. What parameters you want to infer and what is known?**

*Known*
- recombination rate (ρ = 4 N r) for the whole region

*Unknown*
- mutation rate (θ = 4 N μ ) for the whole region 
- time (in coalescent units) that the population size changed
- the population size change

**3. Set up the simulations**
1 decide how many simulations you want to perform
2 here: 1000. In real life > 100000
3 **Important** : for every simulated dataset you will need to change values in the parameters of interest. For example, in the first simulation θ will be 70, population size change time will be 0.01 and population size will be 0.20. 

```
./msABC 122 1000 -t -U 10 100 -r 50 100 -eN -U 0.001 0.5 -U 0.001 1 > expansion.stats
```

```
-t -U 10 100: θ is between 10 and 100 (Uniformly)
-eN -U 0.001 0.5 -U 0.001 1: The population size will change at time t (between 0.001 and 0.5) to a population size that is between 0.001 1 of the present-day population
```

