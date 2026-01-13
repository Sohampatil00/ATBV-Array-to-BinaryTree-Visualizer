ATBV: Array to Binary Tree Visualizer
🔍 Core Concept
ATBV is a web-based visualization tool that instantly converts array representations of binary trees into interactive diagrams. It implements the standard level-order array format used by platforms like LeetCode.
<img width="2952" height="2701" alt="_- visual selection (4)" src="https://github.com/user-attachments/assets/fd910c3e-21ac-47c6-a90a-825ba4b96354" />

🛠️ How It Works (Code Steps)
1. Parse Input
javascript
// Converts "[1,2,3,null,5]" → [1, 2, 3, null, 5]
function parseInput(input) {
    return JSON.parse(input.replace(/'/g, '"'));
}
2. Build Tree
javascript
function arrayToTree(arr) {
    if (!arr.length) return null;
    
    const root = new TreeNode(arr[0]);
    const queue = [root];
    let i = 1;
    
    // Level-order construction
    while (queue.length && i < arr.length) {
        const node = queue.shift();
        
        // Left child
        if (arr[i] !== null) {
            node.left = new TreeNode(arr[i]);
            queue.push(node.left);
        }
        i++;
        
        // Right child
        if (i < arr.length && arr[i] !== null) {
            node.right = new TreeNode(arr[i]);
            queue.push(node.right);
        }
        i++;
    }
    
    return root;
}
3. Render Visualization
javascript
function renderTree(root) {
    // Create hierarchical layout
    const levels = getTreeLevels(root);
    
    // Draw nodes and connectors
    levels.forEach((level, depth) => {
        level.forEach((node, pos) => {
            drawNode(node.val, depth, pos);
            if (node.parent) drawConnector(node, node.parent);
        });
    });
}
<img width="2736" height="1759" alt="_- visual selection (3)" src="https://github.com/user-attachments/assets/e4038f5c-1996-4618-a32b-bcf7309f9a38" />

🎯 Key Features
Real-time conversion: Array → Visual tree

Standard format: Uses LeetCode's [1,2,3,null,5] syntax

Interactive: Click to expand/collapse branches

Zero setup: Runs directly in browser

💻 Usage Example
javascript
// Input (LeetCode format)
[3,9,20,null,null,15,7]

// Gets visualized as:
//        3
//       / \
//      9  20
//        /  \
//       15   7
Live at: atbv.vercel.app



## Screenshots
<img width="2631" height="1467" alt="image" src="https://github.com/user-attachments/assets/a543d8b8-dfe7-409d-902e-da91c6cd5592" />
