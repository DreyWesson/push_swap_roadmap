Mandatory/
└── main/
│   ├── validator/
│   │   ├── ft_parser/
│   │   │   ├── ft_strchr
│   │   │   ├── ft_isdigit
│   │   │   ├── ft_atoi_lg
│   │   │   └── add_node_tail
│   │   └── check_duplicates
│   ├── free_both
│   ├── ft_perror
│   ├── is_sorted
│   └── sort_router/
│   │   ├── list_size
│   │   ├── sort_three/
│   │   │   ├── is_sorted
│   │   │   ├── is_cyclic/
│   │   │   │   ├── min_node_details
│   │   │   │   ├── ft_last_node
│   │   │   │   ├── validate_forward/
│   │   │   │   │   └── ft_last_node
│   │   │   │   ├── validate_backward
│   │   │   │   └── free
│   │   │   ├── list_size
│   │   │   ├── swap_nodes
│   │   │   ├── mid_node_details
│   │   │   │   └── list_size
│   │   │   ├── mover/
│   │   │   │   ├── reverse_rotate
│   │   │   │   ├── swap_nodes
│   │   │   │   └── rotate
│   │   │   ├── sort_three (again for recursion)
│   │   │   └── free
│   │   └── sort_more/
│   │       ├── handle_indexing/
│   │       │   ├── populate_arr
│   │       │   ├── bubble_sort
│   │       │   ├── list_size
│   │       │   └── free
│   │       ├── repeat_push/
│   │       │   └── push
│   │       ├── list_size
│   │       ├── is_sorted
│   │       ├── is_cyclic
│   │       ├── sort_three
│   │       ├── reconfig/
│   │       │   ├── re_calibrator
│   │       │   ├── list_size
│   │       │   ├── min_node_details
│   │       │   ├── special_nodes
│   │       │   ├── exit_cost
│   │       │   ├── target_cost/
│   │       │   │   ├── ft_last_node
│   │       │   │   ├── head_to_tail
│   │       │   │   ├── min_max_handler
│   │       │   │   ├── waterfall
│   │       │   │   └── spring
│   │       │   ├── optimize
│   │       │   ├── priority/
│   │       │   │   ├── both_positive
│   │       │   │   ├── both_negative
│   │       │   │   ├── exit_zero
│   │       │   │   └── target_zero
│   │       │   └──free
│   │       ├── highest_priority/
│   │       │   └── highest_helper
│   │       ├── double_opportunity/
│   │       │   └── helper
│   │       │       ├── repeat_double_rotate
│   │       │       └── repeat_double_reverse
│   │       ├── resort
│   │       │   ├── special_nodes
│   │       │   ├── move_picker
│   │       │   └── free
│   │       ├── push
│   │       ├── exit_moves/
│   │       │   ├── repeat_rotate
│   │       │   └── repeat_reverse
│   │       └── target_moves/
│   │           ├── repeat_rotate
│   │           └── repeat_reverse
│   ├── free
│   └── free_both/
│       └── free_stack
Bonus/
└── main/
    ├── handle_validation/
    │   ├── validator/
    │   ├── free_both/
    │   │   └── free_stack
    │   ├── ft_perror
    │   ├── is_sorted
    │   ├── print_result
    │   └── ft_printf
    ├── free_all/
    │   ├── free_both/
    │   │   └── free_stack
    │   └── free
    ├── is_empty/
    │   ├── ft_strncmp
    │   └── list_size
    └── read_operations/
        ├── ft_strncmp
        ├── swap_nodes
        ├── double_swaps
        ├── push
        ├── rotate
        ├── double_rotate
        ├── reverse_rotate
        └── double_reverse





1. main: Here you'll take care of memory allocation for both stack A and B

Validator /
├── ft_parser
└── check_duplicates
2. validator(int argc, char **argv, t_node **head): (ft_parser & check_duplicates):  You can write a function (ft_parser & check) that checks the number is neg or pos, check if its digit, checks if its not more than int limits, check for duplicates. if valid add to stack
3. free_stack: write a funtion to free_stack
4. free_both: to free both stack at once
5. print_error: a function to print errors
6. is_sorted: checks the number is in ascending order ie next num on the list should be greater than tne prev
7. sort_router: routes the sorting to best handler based on size of list




priority /
├── both_positive
├── both_negative
├── negating_signs
├── exit_zero
└── target_zero
8. priority: a function that runs a loop to adjust the priority of each value in stack_b by comparing exit_cost and target_cost with bunch of if statements. When a exit and target cost are both same sign(+/-) it presents an oppurtunity to rotate the two stacks at the same time but when the target and exit cost are opposite signs then you know they are low priority based on the signs of exit_cost and target_cost. Scenario one is both are positive: if both are positive or both are negative, both are negating_sign, either exit_cost or target_cost is zero

8. both_positive: Although both are positive you wanna save the bigger value as the priority ie if target_cost = 5 and exit_cost = 2, save priority as 5. (Now thinking future me thinking about it Ill probably choose the lesser number as the priority but ive not tried it or know how it will affect the logic of the code)
├── 9 ra (+1 move)      ├── 12 rb,pa (+2 move)
├── 11                  ├── 10
├── 13                  ├── 14
├── 15                  ├── 4
├── 0                   └── 3
├── 1
└── 2 
stack_a                 stack_b
From above if we assume 10 is the existing node. To get it to its target position we will need to rotate on both stacks once. which makes it positive move
9. both_negative: same as both_positive except in the negative direction
├── 9                   ├── 12
├── 11                  ├── 10
├── 13                  ├── 14
├── 15                  ├── 1 rrb, pa
├── 0                   └── 18 rrb
├── 2 rra
└── 3 rra
stack_a                 stack_b
If we assume 1 as the exiting node then it means we reverse rotate on both stack which makes it negative move ie reverse rotate 2ce on stack_a and 
10. exit_zero: if target_cost is >= 0 save target_cost as priority else save priority as target_cost * -1 
├──  4                  ├── 8 pa
├── 11                  ├── 10
├── 13                  ├── 14
├── 15                  ├── 1
├── 0                   └── 18
├── 2
└── 3
stack_a                 stack_b
From above assume 8 is the exiting_node then the exit cost is 0 because its at the top of the stack
12. target_zero: if exit_cost is >= 0 save exit_cost as priority else save priority as exit_cost * -1
13. negating_signs: if exit_cost or target_cost are opposite signs ie if target_cost is maybe -3 and exit_cost is +4. then sum the abs val of target_cost and abs val of exit_cost and multiply there sum by -1 and save as the priority
├── 9 ra                ├── 12
├── 11 ra               ├── 10
├── 13 ra               ├── 1
├── 15                  ├── 14 rrb
├── 0                   └── 18 rrb
├── 2
└── 3
stack_a                 stack_b
Assume, 14 is the exiting_node. so since you are rotating the two stacks in the opposite directions this will get the least priority

special_nodes /
├── min_node_details
├── mid_node_details
└── max_node_details
1. min_node_details: this keep track of the position of node with minimum value on a stack. Here you will save the node details like position and value. So, you have to have a pos variable init to zero and increment as you loop through. Tip: u can use max_int as the initial minimum value.
2. mid_node_details: as the name implies. u need this function so as to calculate if the position you are trying to access can be quickly accessed from the top(ra) or tail(rra). There to implement? divide the list_size by 2, then loop through till the value of the (list_size by 2) == pos of the current node in the loop. when it is save the node details as the mid_node
3: max_node_details: same logic as min_node_details except here u are looking for the max instead min. use min_int limit too.
Illustration:
├── 3
├── 4        
├── 5        
├── 6      
├── 7  * mid_node    
├── 9  * max_node    
├── 0  * min_node    
├── 1      
└── 2



target_cost /
├── ft_last_node
├── head_to_tail
├── min_max_handler
├── waterfall
└── spring
14. target_cost: Here we wanna find the position to slot the exiting value from stack_b to stack_a. And to this end we need to take care of all scenario and return true if a position is found. Also, worthy of note is that target cost has to be fullproof to situation where stack_a is_sorted or cyclicly_sorted
15: head_to_tail: Here you get the value of the last node and compare with the value of the first node on top of the stack. Check if exiting node should be placed between them and return true if it should
Illustration:
├── *** target_pos
├── 5 * top node        └── 3 or 4 * exiting_node
├── 6
├── 7
├── 9
├── 0
├── 1
└── 2 * last node
stack_a                 stack_b

16. min_max_handler: Here is a scenario where the exiting node could lower/higher than the pre-existing lower/ pre-existing higher number on stack_a. e.g lets say we have 2/14 as the min/max on stack_a - if the node exiting from stack_b is either 0/15 then it needs to be placed between them. this function searches for the min and max on stack_a and places the exiting node there
Illustration:
├── 5 * top node        └── 0 or 10 * exiting_node
├── 6
├── 7
├── 9
├── *** target_pos
├── 1
└── 2 * last node
stack_a                 stack_b






├── 5                            └── 2
├── 6                            
├── 9 * buggy pivot                        
├── 7 * the bug                         
├── 0 * current pivot 
├── 1                                      
└── 3                            
stack_a                          stack_b
It is important to note that min-node is our pivot point for waterfall and spring.
This is important because if we choose different pivot point, then our algorithm may be buggy. Why?
If we change our pivot point to max_node rather than the min_node we were using in water fall then there will
be a bug. So in choosing a pivot you can pick either the max/min but not both. That way we will have a proper
handshake between the max and min node (ie back-back)

since the target pos is not between max and min, and not between top and tail of stack we need to then search through the stack. using waterfall and spring
17. waterfall: Here you wanna search the stack from min_node-down(because minimum can be in any position
when stack is cyclically sorted) and see in which position the exiting_node fits by comparing the 
exiting_node value with current and next node values. if it fits between okay great but it not enough 
to know that. we also need to know which move is optimal to get to that positon that is;
is it rra or ra etc. Therefore, the exiting _node target_cost will be the 
(current_node index - list_size + 1) if target position is greater than the mid_pos else if it is 
lesser or equal to the mid_pos the target_cost will simply be the next_node index;

example: assume 8 is the value of the exiting node, in the stack below you will realise that the 8 target should be between 7 and 9

├── 5                            └── 2 / 8
├── 6                            
├── 7
├── *** target_pos                             
├── 9 * mid pos && max node                          
├── 0 * waterfall ↓↓↓ | min node    
├── 1                            
├── *** target_pos               
└── 3                            
stack_a                          stack_b
In case of 2, since mid_pos is 4 and our target pos is greater than mid_pos (which means the best move is rra), we need to save how many rra move to the target_cost which will be target_pos-7(which is current position 13 is occupying) - list_size + 1. Therefore target_cost will be 7 - (7 + 1) = -1. So just one RRA move and we can slot 2 in stack_a.
In case of 8, since mid_pos is 4 and our target pos is lower than mid_pos (which means the best move is ra), we need to save how many ra move to the target_cost which will be the index of the next_node.
18. Spring: Here you wanna move from the min-mode to the max-node, by using prev (I assume you are using doubly linked list).
Then compare the value u moved into with the value of max node you saved with the special_node functions.
This logic ensures the bug we below doesn't slip through the crack.
├── 5                             └── 2
├── 6                            
├── 9 * buggy pivot | max node                       
├── 7 * the bug | prev                        
├── 0 * current pivot | min-node
├── 1                                      
└── 3
So, from our min-node, when we move to prev, the node will be 7. Now when we compare the value of prev and
max-node value, we immediately catch. the bug. But in a situation where the bug is removed like below
├── 5                                       └── 2
├── 6                            
├── 9 * buggy pivot | max node | prev                                             
├── 0 * current pivot | min-node
├── 1                                      
└── 3
when we compare the value of prev node with the value of max-node then we will see they are equal. Now we
can calculate the target cost same way we did waterfall but in the opposite direction. Check where exiting_node
fits from max-node to the top of the stack. When you do, check its position relative to the mid-pos so as to determine
the optimal move. So if the target position of the exiting is <= mid-node then we save the index of current node as target_cost
else we save the target_cost as current index - list_size



reconfig /
├── re_calibrator
├── list_size
├── min_node_details
├── special_nodes
├── exit_cost
├── target_cost
├── optimize
├── priority
└── free
After every exit from stack_b to stack_a we gotta reconfigure and reset our indexes and other things.
1. recalibrator: This loops over stacks and changes the indexes on both stacks since we've now added a
new value. So, it will be helpful to write the function such that it's dynamic and works with any stack.
so we can call it on both stack_a and stack_b
2. List_size: we also need to get the sizes of both stacks. since one value has been removed and gained in the other.
Note it will be performant to call list_size again. we can just deduct one from our list size of stack_b and 
one to the list_size of stack_a
3. Mid_node_details: we need to get the mid_node pos of stack_b also. so we can decide the best exit.
4. special_nodes: we need to get the new values of min, mid and max node.
5. exit_cost: Here like target_cost but not as robust. Here we just need to decide if the exiting node is above
the mid-pos or beneath. if it is above we know the best move is RB so we save the index of the current node as the exit_cost
but if it is greater than mid-pos then we will substract the size of stack_b from current node index.




is_cyclic /
├── min_node_details
├── ft_last_node
├── validate_forward
├── validate_backward
└── free
The whole is_cyclic function is to check if the stack is sorted even though not top down e.g
├── 3
├── 4        
├── 5        
├── 6      
├── 7     
├── 9     
├── 0  rra   
├── 1  rra    
└── 2  rra
The above is cyclically sorted because if you reverse rotate thrice it will be sorted. I wont dwell too much here cos the nested function are named intuitively.



handle_indexing /
├── populate_arr
├── bubble_sort
├── list_size
└── free
Here we do a sneak peak into the list to see what position numbers on our list should be when sorted. So, we create an array and populate it with the values on our list. Then, perform a bubblesort. Then run a loop to the stack_a and save this position on each struct accordingly. Note that this is done after we have validated the input and populated our stack_a. Remember to free this array as it as served its purpose already.




├── double_swaps/
│   ├── swap_nodes
│   └── ft_printf
├── repeat_rotate/
│   └── rotate
├── repeat_double_rotate/
│   └── repeat_double_rotate
├── repeat_double_reverse/
│   └── repeat_double_reverse
├── repeat_push/
│   └── push
├── repeat_reverse/
│   └── reverse
Just bunch of functions for rotating, reversing and all the operations allowed.

highest_priority /
└── highest_helper
Here, we want to know which exiting node has the highest priority. Here we can initialise a variable(max) to int_max value. Then we loop through stack_b and compare priority the node with the highest priority is aved and returned at the end of the loop. So, for every loop we check current node priority is greater than current highest_priority and save the ne highest prioritized node and also change the value of the initialized variable(max)










ft_parser /
├── ft_strchr
├── ft_isdigit
├── ft_atoi_lg
└── add_node_tail

free_both /
└── free_stack

sort_router /
├── list_size
├── sort_three
└── sort_more

sort_three /
├── is_sorted
├── is_cyclic
├── list_size
├── swap_nodes
├── min_node_details
├── mover
├── sort_three (again for recursion)
└── free

sort_more /
├── handle_indexing
├── repeat_push
├── list_size
├── is_sorted
├── is_cyclic
├── sort_three
├── reconfig
├── highest_priority
├── double_opportunity
├── exit_moves
├── target_moves
├── push
├── is_sorted && is_cyclic
├── resort
├── free_both
└── free


swap_nodes /
└── ft_printf

double_swaps /
├── swap_nodes
└── ft_printf

mid_node_details /
└── push

repeat_push /
└── push








is_cyclic /
├── min_node_details
├── ft_last_node
├── validate_forward
├── validate_backward
└── free

validate_forward /
└── ft_last_node

mover /
├── reverse_rotate
├── swap_nodes
└── rotate

reconfig /
├── re_calibrator
├── list_size
├── min_node_details
├── special_nodes
├── exit_cost
├── target_cost
├── optimize
├── priority
└── free



repeat_rotate /
└── rotate

repeat_double_rotate /
└── repeat_double_rotate

repeat_double_reverse /
└── repeat_double_reverse

repeat_push /
└── push

repeat_reverse /
└── reverse

helper /
├── repeat_double_rotate
└── repeat_double_reverse

double_opportunity /
└── helper

exit_moves /
├── repeat_rotate
└── repeat_reverse

target_moves /
├── repeat_rotate
└── repeat_reverse

push /
├── del_node
├── add_node_head
└── ft_printf

resort /
├── special_node
├── move_picker
└── free

move_picker /
├── list_size
├── repeat_rotate
└── repeat_reverse

double_reverse /
├── repeat_rotate
└── ft_printf

rotate /
├── del_node
├── add_node_tail
└── ft_printf

double_rotate /
├── repeat_rotate
└── ft_printf

reverse_rotate /
├── ft_last_node
├── del_node
├── add_node_head
└── ft_printf

bonus/main /
├── handle_validation
├── get_next_line
├── is_empty
├── read_ops
├── free_all
├── free
├── print_result
├── ft_perror
├── ft_perror
└── free

handle_validation /
├── validator
├── free_both
├── ft_perror
├── is_sorted
├── print_result
├── free_both
└── ft_printf

free_all /
├── free_both
└── free

is_empty /
├── ft_strncmp
└── list_size

read_operations /
├── ft_strncmp
├── swap_nodes
├── double_swaps
├── push
├── rotate
├── double_rotate
├── reverse_rotate
└── double_reverse
