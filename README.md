# form-action-of-a-page-to-another-page-in-NEXT.js-React.js

# To Transfer data from Ajij.js to PaySlip.jsv  

## Ajij.js

```
import { useState } from "react";
import {useRouter] from "next/router";

const Ajij = ({action = "/PaySlip"}) => {
  const router = useRouter();

  const [user, setUser] = useState({ name: "", email: "" });

  const handleInputFieldChange = (e) => {

    const fieldName = e.target.name;
    const fieldValue = e.target.value

    setUser({ ...user, [fieldName]: fieldValue });

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
# PaySlip.js

```
import {useRouter} from "next/router";
const PaySlip =() =>{
  const router = useRouter();
  const {name,email} = router.query;
} 
export default PaySlip;
```  






