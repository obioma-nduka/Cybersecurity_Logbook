### 🧑‍🦲 **Guest**

---

**✅ Can do**

List every action a *Guest* can perform, with the page or endpoint.

* “Can view public resource list — `/`”
* “Can access login form — `/login`”
* “Can view registered reservations without identity — `/` (spec 8)”

---

**❌ Cannot do**

List every action that a *Guest* is blocked from doing.

* “Cannot access `/reservation` (redirect to login)”
* “Cannot POST `/reservations`”
* “Cannot access any `/admin/*` pages”
* “Cannot access reserver profile page `/profile`”

---

### 🧑‍💼 **Reserver**

---

**✅ Can do**

List actions a *Reserver* can do according to specs + actual test results.
Include visible pages **and** API endpoints.


* “Can book a resource — `http://localhost:8003/resources`”
* “Can add a reservation — `http://localhost:8003/reservation`”
* “Can view own profile page — `http://localhost:8003/`”
* “Can show list of resources — `http://localhost:8003/`”
* “Can delete its own reservation — `http://localhost:8003/reservation?id=3`”

---

**❌ Cannot do**

List actions a *Reserver* is correctly blocked from.


* “Cannot access admin user list — `http://localhost:8003/`”
* “Cannot delete other users — `http://localhost:8003/d`”
* “Cannot modify resources (spec says admin only)”
* “Cannot escalate privileges via hidden form fields”

---

### 🧑‍💼🛡️ **Administrator**

---

**✅ Can do**

List actions an *Administrator* can perform.


* “Can add a resource — `http://localhost:8003/resources`”
* “Can create a reservation — `http://localhost:8003/reservation`”
* “Can delete a reservation — `http://localhost:8003/reservation?id=2`”
* “Can manage all reservations — `http://localhost:8003/reservation?id=1`”
* “Can view all users (spec 4)”

---

**❌ Cannot do**

List prohibited behaviors, if any, or incorrect implementation issues.


* “Cannot book a resource if the system incorrectly blocks admins (bug?)”
* “Cannot perform an action because the UI has no link (but API allows?) — flag as ⚠️”

---
