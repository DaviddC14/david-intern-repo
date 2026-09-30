# Clean Code Principles

## Core Principles Summary
* **Simplicity:** Keep code as simple as possible. Avoid "clever" one-liners if they make the logic harder to grasp. The goal is clarity, not showing off language features.
* **Readability:** Code is read far more often than it is written. Use highly descriptive, pronounceable variable and function names so the code reads like a well-written article.
* **Maintainability:** Future developers (including you in 6 months) should be able to navigate and modify the code easily. Follow principles like Single Responsibility—a function should do one thing and do it well.
* **Consistency:** Follow established style guides and project conventions (e.g., using Prettier or ESLint). If the team names boolean variables starting with `is` or `has`, stick to that pattern everywhere.
* **Efficiency:** Write performant, optimized code without premature over-engineering. Focus on clean architecture first; optimize for performance only when it becomes a measured bottleneck.

---

## Messy Code Example
Here is a typical example of poorly written backend JavaScript handling a database request:

```javascript
const d = require('db');

function getD(req, res) {
    d.query("SELECT * FROM users WHERE id=" + req.params.id, function(err, r) {
        if(err) res.send(500);
        else {
            if(r.length > 0) {
                d.query("SELECT * FROM posts WHERE uid=" + r[0].id, function(err2, r2) {
                    if(err2) res.send(500);
                    else {
                        res.json({u: r[0], p: r2});
                    }
                });
            } else res.send(404);
        }
    });
}