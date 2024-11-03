# Traveling Salesman Problem

This repository contains an implementation of a Genetic Algorithm (GA) designed to solve the Traveling Salesman Problem (TSP). The GA uses several techniques to optimize the search for the best path connecting a set of cities.

## Instances
These are the data used for the tsp problem
| Filename    | Country       | Number of Cities | 
|-------------|---------------|------------------|
| china.csv   | China         | 726               | 
| italy.csv   | Italy         | 46               | 
| russia.csv  | Russia        | 167               |
| us.csv      | United States | 326               |
| vanuatu.csv | Vanuatu       | 8               |


## Solution
The proposed solution begins with a **Greedy Algorithm*** to generate an initial approximation. This solution is then further optimized using a **Genetic Algorithm (GA)**. Since the GA builds directly on the Greedy Algorithm’s results, we discuss only the GA as the primary solution, with the Greedy Algorithm serving as its initialization step.



## Main Features of the Algorithm
The Genetic Algorithm has been implemented with the following key characteristics:
- **Starting point**: The algorithm uses the result of a Greedy algorithm combined with random initial solutions
- **Hypermodern Genetic Algorithm**: This approach alternates between mutation and recombination 

- **Steady State Strategy**: The algorithm maintains a balance between old and new solutions, allowing the offspring to partially replace the population 

- **Mutation**: Inversion Mutation

- **Recombination**: Inver Over Crossover

- **Parent selection**: Fitness proportional, randomly selecting individuals and choosing the best ones


**Main steps:**

1. **Initialization**: Create an initial population of potential solutions (paths). 


2. **Selection**: Choose parent solutions from the current population

3. **Crossover** or **Mutation**: Apply the genetic operator according to a specific probability value (**strength**)

4. **Replacement**: Form a new generation by replacing some individuals in the population with the offspring generated

5. **Termination**: Stop the process after a specified number of generations

**Details:**
- The initialization step involves creating an initial population that includes a certain percentage of greedy solutions obtained from the greedy algorithm (specified by **percentage_greedy**) alongside randomly generated individuals
- There is a **Self-adaptive approach** related to the choice between Mutation and Ricombination (**strength**). At the beginnig it favors exploration with an higher probability to apply crossover, while going on with generations it favors exploitation, with an higher chance to have mutation.


## Main functions

- **greedy_tsp(dist_matrix, init_city)**: Generates an initial greedy solution based on the distance matrix

- **fill_population(percentage, size, init_solution, init_city)**: Initializes the population with a mix of greedy and random solutions

- **parent_selection(population)**: Selects parents randomly from the population and takes the best ones.

- **inverOver(p1, p2, init_city)**: Performs the inver over crossover operation

- **inversion_mutation(p, init_city)**: Reverses segments of the path to create mutations
- **genetic_algorithm(init_city,init_solution, percentage_greedy, POPULATION_SIZE, OFFSPRING_SIZE, MAX_GENERATIONS, mutation_type, xover_type)**:
This is the main function that implements the genetic algorithm. It manages the evolution of the population over multiple generations.

- **Parameters**:
  - `init_solution`: Initial greedy solution.
  - `percentage_greedy`: The percentage of the population that should consist of greedy solutions.
  - `POPULATION_SIZE`: Total number of individuals in the population.
  - `OFFSPRING_SIZE`: Number of offspring generated in each generation.
  - `MAX_GENERATIONS`: The maximum number of generations to run the algorithm.
  - `init_city`: The starting city.
  - `mutation_type`: The mutation function to apply.
  - `xover_type`: The crossover function to apply.
- **apply_instances**: Runs all the several instances with specific settings (population size, offspring size..etc) for each country


## Results
| Country                 |Known best distance (km) | Best result found (km) | (greedy percentage, pop_size, offspring_size, generations) | Number of Steps |
|---------------------------|------------------|-----------------|---------------------|---------------------|
| **China**           |     -     |   62740.15            | (0.2, 500, 300, 1000) |726 |
| **Italy** |   4172.76     |4172.763 | (0.4, 300, 200, 1000)|46
| **Russia** |   32722.5       |          38829.236     |  (0.2, 500, 300, 1000) | 167        |
| **US** |   39016.62     |        45722.84       |(0.2, 500, 300, 1000) |    326        |
| **Vanuatu** |    1345.54    |     1345.545          |  (0.2, 200, 100, 100)   | 8      |

