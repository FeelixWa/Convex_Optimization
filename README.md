# Optimization Algorithms in Julia

This repository provides implementations of various optimization algorithms using Julia. It includes gradient-based methods and Newton's methods for optimizing functions of one or more variables.

## Features

- **Gradient Descent**: Basic and with optimal step size.
- **Newton's Method**: Pure Newton's method, cyclic Newton's method, and SR1 quasi-Newton method.
- **Gradient Calculation**: Functions for numerical gradients and Hessians.

## Installation

Ensure you have Julia installed. Clone this repository and use the provided code in your Julia environment.

## Usage

1. **Define the Objective Function**: Implement your function to optimize, e.g., `f_2` in the provided code.
2. **Run Optimization Algorithms**: Use the functions provided for different optimization methods.

### Example

```julia
using LinearAlgebra

# Define the objective function
function f_2(X)
    A = [4 1 2; 1 5 3; 2 3 6]
    B = [1, 1, 1]
    return 0.5 * (X' * A * X) + B' * X
end

# Run optimization algorithms
x_0 = zeros(3)
println("Optimal X: ", inv(A) * B')
println("X after gradient descent: ", gradient_descent_n(f_2, 3, 10, 0.1))
println("X after gradient descent with Armijo rule: ", gradient_descent_opt_2(f_2, 3, 10))
println("X after pure Newton method: ", newton_pure(f_2, 3, x_0, 10))
println("X after cyclic Newton method: ", newton_cyclic(f_2, 3, x_0, 100, 10))
println("X after SR1 quasi-Newton method: ", newton_SR1(f_2, 3, x_0, 10))
