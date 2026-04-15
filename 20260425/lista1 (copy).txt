using JuMP
using HiGHS

function responde(model, x, P)
    print("\n")
    status = termination_status(model)

    if status == MOI.INFEASIBLE
        println("O problema é INVIÁVEL.")
    elseif status == MOI.DUAL_INFEASIBLE
        println("O problema é ILIMITADO.")
    else
        println("O problema possui solução ótima.")
        println("z = ", objective_value(model))
        for j in P
            println("x[$j] = ", value(x[j]))
        end
    end
    print("\n")
end

function letra_a()
    P = [1,2]

    v = [3, 1] # objective
    d = [6, 9] # cota <=
    c = [
        2 1
        1 3
    ]

    
    model = Model(HiGHS.Optimizer) 

    @variable(model, x[P] >= 0)

    @objective(model, Max, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("a: ")
    responde(model, x, P)
end

function letra_b()
    P = [1,2]

    v = [1, 1] # objective
    d = [4, 5] # cota <=
    c = [
        1  1
        1 -1
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Max, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("b: ")
    responde(model, x, P)
end

function letra_c()
    P = [1,2]

    v = [4, 1] # objective
    d = [16, 12] # cota <=
    c = [
        8 2
        5 2
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Max, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("c: ")
    responde(model, x, P)
end

function letra_d()
    P = [1,2]

    v = [-1, 3] # objective
    d = [4, -4] # cota <= (segunda restrição multiplicada por -1 para virar <=)
    c = [
         1 -1
        -1 -2
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Max, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("d: ")
    responde(model, x, P)
end

function letra_e()
    P = [1,2]

    v = [3, 5] # objective
    d = [15, 10] # cota <=
    c = [
        3 5
        5 2
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Max, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("e: ")
    responde(model, x, P)
end

function letra_f()
    P = [1,2]

    v = [3, -2] # objective
    d = [1, -4] # cota <= (segunda restrição multiplicada por -1 para virar <=)
    c = [
         1  1
        -2 -2
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Max, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("f: ")
    responde(model, x, P)
end

function letra_g()
    P = [1,2]

    v = [1, 4] # objective
    d = [10, 9] # cota <=
    c = [
        2 1
        1 3
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Max, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("g: ")
    responde(model, x, P)
end

function letra_h()
    P = [1,2]

    v = [3, 2] # objective
    d = [6, 8] # cota <=
    c = [
        2 2
        1 3
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Max, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("h: ")
    responde(model, x, P)
end

function letra_i()
    P = [1,2]

    v = [1, 1] # objective
    d = [2, 3, 9, 18] # cota <=
    c = [
        -3 1
         0 1
         1 2
         3 1
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Max, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("i: ")
    responde(model, x, P)
end

function letra_j()
    P = [1,2]

    v = [1, 3] # objective
    d = [4, 6, 3, 18] # cota <=
    c = [
        0 1
        1 1
        1 0
        5 1
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Max, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("j: ")
    responde(model, x, P)
end

function letra_k()
    P = [1,2]

    v = [3, 2] # objective
    d = [-3, -2, -6, 3, 30] # cota <= (primeiras três multiplicadas por -1 para virar <=)
    c = [
        -1  0
         0 -1
        -1 -1
         1 -1
         3  5
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Max, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("k: ")
    responde(model, x, P)
end

function letra_l()
    P = [1,2]

    v = [2, 1] # objective
    d = [10, -60, 18, 44] # cota <= (segunda multiplicada por -1 para virar <=)
    c = [
         0  1
        -2 -5
         1  1
         3  1
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Max, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("l: ")
    responde(model, x, P)
end

function letra_m()
    P = [1,2]

    v = [1, 1] # objective
    d = [-9, -12] # cota <= (multiplicadas por -1 para virar <=)
    c = [
        -2 -3
        -4 -3
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Min, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("m: ")
    responde(model, x, P)
end

function letra_n()
    P = [1,2]

    v = [3, 2] # objective
    d = [-10, -12, -12] # cota <= (multiplicadas por -1 para virar <=)
    c = [
        -5 -1
        -2 -2
        -1 -4
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Min, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("n: ")
    responde(model, x, P)
end

function letra_o()
    P = [1,2]

    v = [3, 2] # objective
    d = [-3, -2, -6, 3] # cota <= (três primeiras multiplicadas por -1 para virar <=)
    c = [
        -1  0
         0 -1
        -1 -1
         1 -1
    ]

    model = Model(HiGHS.Optimizer)

    @variable(model, x[P] >= 0)

    @objective(model, Min, v'x)

    @constraint(model, c * x .<= d)

    set_silent(model)
    optimize!(model)
    print("o: ")
    responde(model, x, P)
end

letra_a()
letra_b()
letra_c()
letra_d()
letra_e()
letra_f()
letra_g()
letra_h()
letra_i()
letra_j()
letra_k()
letra_l()
letra_m()
letra_n()
letra_o()

print("acabou")