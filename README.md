# CI2024_lab1

To solve the Set Cover optimization problem, I tried implementing several local search algorithms to be able to compare the solutions they found in different scenarios of the problem:
- Random Mutation Hill Climbing
- Hill Climbing with a more powerful tweak
- Hill Climbing with a more powerful tweak and 1 out of 5 rule
- Simulated Annealing
- Iterated Local Search
- Iterated Local Search with Simulated Annealing
- Tabu Search
- Iterated Local Search with Tabu Search
- Iterated Local Search with 1 out 5 rule
  
To solve the instances of problem 1-3, which are characterized by a smaller universe size and fewer sets, I decided to set the number of steps to 10,000. 
For the instances of problem 4-6, I chose to reduce the number of steps to 100 in order to limit the execution time for each algorithm to a few minutes. 
I made this decision because, with a higher number of iterations, I could have further improved the fitness obtained by each algorithm but I would have had to wait for hours. 
Ultimately, what matters in this analysis is the relative effectiveness of the algorithms in different scenarios rather than the precise search for the best possible fitness achieved by each algorithm.

1) As for the instance 1 of the problem, none of the implemented algorithms are able to improve the initial solution, which was generated by taking all the available subsets.
2) As for the instance 2 of the problem, the algorithms that achieved the highest fitness are:
- Iterated Local Search
- Iterated Local Search with Simulated Annealing
- Iterated Local Search with Tabu Search
3) As for the instance 3 of the problem, the algorithm that achieved the highest fitness is:
- Hill Climbing with a more powerful tweak and 1 out of 5 rule
4) As for the instance 4 of the problem, the algorithms that achieved the highest fitness are:
- Iterated Local Search
- Iterated Local Search with Simulated Annealing
- Iterated Local Search with Tabu Search
5) As for the instance 5 of the problem, the algorithms that achieved the highest fitness are:
- Iterated Local Search
- Iterated Local Search with Simulated Annealing
- Iterated Local Search with Tabu Search
6) As for the instance 6 of the problem, the algorithms that achieved the highest fitness are:
- Iterated Local Search
- Iterated Local Search with Simulated Annealing
- Iterated Local Search with Tabu Search
- Iterated Local Search with 1 out 5 rule

Overall, analyzing the behavior of the different algorithms in various scenarios, if I had to choose an algorithm to move forward with, I would opt for **Iterated Local Search with Simulated Annealing**.

Using **Iterated Local Search** where each local search phase is performed by **Simulated Annealing** offers several advantages, particularly in terms of balancing exploration and exploitation in optimization problems. 
Simulated Annealing is designed to escape local minima by accepting worse solutions with a certain probability, especially at higher temperatures. 
When combined with ILS, this allows the algorithm to explore a broader range of solutions, making it less likely to get stuck in suboptimal areas of the search space.
ILS restarts the search process after each local search, potentially moving to entirely different regions of the search space. 
With SA guiding the local search, each restart begins from a diverse area, enhancing the overall exploration ability of the algorithm.

Simulated Annealing starts with a higher level of exploration (accepting worse solutions) and progressively focuses more on exploitation as the temperature decreases allowing the algorithm to fine-tune solutions as it converges. 
This provides a smooth transition from wide exploration to focused optimization.
Within ILS, this feature allows each local search phase to refine the solutions more effectively as SA ensures that even the local searches explore sufficiently before focusing on local improvements.

The combination of ILS and SA creates a dynamic balance between local and global search. 
ILS helps to move across different regions of the solution space (global search) while Simulated Annealing allows for deep, focused exploration of each region (local search).
This results in an algorithm that can avoid premature convergence on suboptimal solutions and increases the likelihood of finding global optima.

SA is known for its robustness in navigating complex fitness landscapes with many local minima. 
Its probabilistic acceptance criteria allow it to jump out of local minima, even in highly non-convex or noisy problem landscapes.
ILS benefits from this ability because each local search is capable of making meaningful progress even in rugged fitness landscapes, improving the overall efficiency of the algorithm in solving challenging optimization problems.

By incorporating the temperature control mechanism of Simulated Annealing, ILS can dynamically adjust the search precision. 
Higher temperatures lead to larger steps and broader exploration while lower temperatures allow for more precise adjustments and exploitation.
This feature is especially useful for multi-modal optimization problems, where diverse regions of the search space need to be explored first followed by a fine-tuning process.

The main strength of Simulated Annealing within the ILS framework is its ability to escape from local minima. 
In traditional local search methods like Hill Climbing, once a local minimum is reached, the search may stagnate. SA, however, continues to accept worse solutions with some probability, giving it the potential to move away from local minima and explore new regions.
This escape mechanism increases the robustness of the ILS approach allowing it to deal with complex optimization problems that would otherwise trap simpler local search methods.

ILS operates by restarting the search process after each local search phase and Simulated Annealing provides a progressive refinement mechanism within each phase. 
After each iteration, ILS uses the results of the previous local search (SA) to guide further exploration.
This iterative process enables gradual improvements over time increasing the chances of finding better solutions as the algorithm progresses.
