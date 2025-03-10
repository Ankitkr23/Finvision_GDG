import numpy as np

class RangeTree:
    def __init__(self, data):
        self.data = data
        self.size = len(data)
        self.min_tree = np.full(4 * self.size, float('inf'))
        self.max_tree = np.full(4 * self.size, float('-inf'))
        self._construct(0, 0, self.size - 1)

    def _construct(self, idx, left, right):
        if left == right:
            self.min_tree[idx] = self.max_tree[idx] = self.data[left]
            return
        mid = (left + right) // 2
        self._construct(2 * idx + 1, left, mid)
        self._construct(2 * idx + 2, mid + 1, right)
        self.min_tree[idx] = min(self.min_tree[2 * idx + 1], self.min_tree[2 * idx + 2])
        self.max_tree[idx] = max(self.max_tree[2 * idx + 1], self.max_tree[2 * idx + 2])

    def _get_min(self, idx, l, r, ql, qr):
        if qr < l or ql > r:
            return float('inf')
        if ql <= l and r <= qr:
            return self.min_tree[idx]
        mid = (l + r) // 2
        return min(
            self._get_min(2 * idx + 1, l, mid, ql, qr),
            self._get_min(2 * idx + 2, mid + 1, r, ql, qr)
        )

    def _get_max(self, idx, l, r, ql, qr):
        if qr < l or ql > r:
            return float('-inf')
        if ql <= l and r <= qr:
            return self.max_tree[idx]
        mid = (l + r) // 2
        return max(
            self._get_max(2 * idx + 1, l, mid, ql, qr),
            self._get_max(2 * idx + 2, mid + 1, r, ql, qr)
        )

    def min_range(self, ql, qr):
        if ql < 0 or qr >= self.size or ql > qr:
            return "Invalid range"
        return self._get_min(0, 0, self.size - 1, ql, qr)

    def max_range(self, ql, qr):
        if ql < 0 or qr >= self.size or ql > qr:
            return "Invalid range"
        return self._get_max(0, 0, self.size - 1, ql, qr)

    def add_value(self, val):
        self.data.append(val)
        self.size += 1
        self.min_tree = np.full(4 * self.size, float('inf'))
        self.max_tree = np.full(4 * self.size, float('-inf'))
        self._construct(0, 0, self.size - 1)

def launch():
    try:
        n, q = map(int, input("Enter number of prices and queries: ").split())
        items = list(map(int, input(f"Enter {n} prices: ").split()))
        if len(items) != n:
            print("Mismatch in price count.")
            return

        tree = RangeTree(items)
        print("\nCommands:\n A x → Add x\n S l r → Min\n R l r → Max\n")

        for _ in range(q):
            cmd = input(">> ").split()
            if not cmd:
                continue
            action = cmd[0]

            if action == "A" and len(cmd) == 2:
                tree.add_value(int(cmd[1]))
                print(f"Added: {cmd[1]}")
            elif action == "S" and len(cmd) == 3:
                l, r = int(cmd[1]), int(cmd[2])
                print(f"Min({l}-{r}) =", tree.min_range(l, r))
            elif action == "R" and len(cmd) == 3:
                l, r = int(cmd[1]), int(cmd[2])
                print(f"Max({l}-{r}) =", tree.max_range(l, r))
            else:
                print("Invalid command.")
    except Exception as e:
        print(f"Error: {e}")

if __name__ == "__main__":
    launch()
