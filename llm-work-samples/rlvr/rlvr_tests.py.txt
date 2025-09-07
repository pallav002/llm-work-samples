# rlvr_tests.py
# Simple RLVR-style unit test: the candidate must implement even_only(nums) -> list of even ints
# Reward: 1.0 for passing all tests, 0.0 otherwise.

def even_only(nums):
    # Candidate function should return even numbers only in original order.
    # This is a placeholder; real candidate output will be executed by harness.
    return [x for x in nums if isinstance(x, int) and x % 2 == 0]

# Test harness
def reward_fn(candidate_fn):
    tests = [
        ([1,2,3,4], [2,4]),
        ([0,-2,5,11,14], [0,-2,14]),
        ([], []),
        ([2.0, 4], [4])  # rejects floats -> only integers
    ]
    try:
        for inp, expected in tests:
            out = candidate_fn(inp)
            if out != expected:
                return 0.0
        return 1.0
    except Exception:
        return 0.0

# If running locally for self-check
if __name__ == "__main__":
    print("Reward:", reward_fn(even_only))
