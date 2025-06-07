# EXP-4-MINIMAX
def minimax(position, depth, maximizing_player, evaluate, get_children):
    if depth == 0 or is_terminal(position):
        return evaluate(position)

   if maximizing_player:
        max_eval = float('-inf')
        for child in get_children(position, True):
            eval = minimax(child, depth - 1, False, evaluate, get_children)
            max_eval = max(max_eval, eval)
        return max_eval
    else:
        min_eval = float('inf')
        for child in get_children(position, False):
            eval = minimax(child, depth - 1, True, evaluate, get_children)
            min_eval = min(min_eval, eval)
        return min_eval

