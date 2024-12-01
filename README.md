# Intellect-Pairing-Challenge

At a vibrant educational camp, there are N enthusiastic learners, each possessing a distinct level of intellect represented by dᵢ. The camp leader faces an intriguing challenge: they wish to pair up each student, ensuring that every student is in one pair only, and that the total intellect of each pair matches. Additionally, the leader defines the efficiency of a pair of learners i and j as the product of their intellect, dᵢ * dⱼ. Your task is to calculate the total efficiency for all the pairs formed. If it’s not feasible to create such pairs with equal total intellect, you must return -1. Can you assist the camp leader in solving this problem and optimizing the effectiveness of the learners’ collaboration?

def calculate_total_efficiency(N, intellect_levels):
    # Sort the intellect levels
    intellect_levels.sort()
    
    # Target sum is the sum of the smallest and largest element
    target_sum = intellect_levels[0] + intellect_levels[-1]
    
    total_efficiency = 0
    
    # Use two pointers to form pairs
    left, right = 0, N - 1
    while left < right:
        if intellect_levels[left] + intellect_levels[right] != target_sum:
            return -1
        total_efficiency += intellect_levels[left] * intellect_levels[right]
        left += 1
        right -= 1
    
    return total_efficiency

# Input
N = int(input())
intellect_levels = list(map(int, input().split()))

# Output
print(calculate_total_efficiency(N, intellect_levels))
