# form-action-of-a-page-to-another-page

# To Transfer data from Ajij.js to User.jsv  

## Ajij.js

```
import { useState } from "react";
import {useRouter] from "nest/router";

const Ajij = ({action = 'User"}) => {
  const router = useRouter();

  const [user, setUser] = useState({ name: "", email: "" });

  const handleInputFieldChange = (e) => {

    const fieldName = event.target.name;

    setUser({ ...user, [fieldName]: event.target.value });

  };

  const handleSubmit = (e) => {

    e.preventDefault();

    router.push({
      pathname:action,
      query: {
        User:user
      },
   })

 };

  return (

    <div>

      <h2>Create User</h2>

      <form onSubmit={handleSubmit}>

        <div>

          <label htmlFor="name">

            Name

            <input

              type="text"

              id="name"

              name="name"

              value={user.name}

              onChange={handleInputFieldChange}

              required

            />

          </label>

        </div>

        <div>

          <label htmlFor="email">

            Email

            <input

              type="email"

              id="email"

              name="email"

              value={user.email}

              onChange={handleInputFieldChange}

              required

            />

          </label>

        </div>

        <button type="submit">Create User</button>

      </form>

    </div>

    );

  };
export default Ajij;
```  




