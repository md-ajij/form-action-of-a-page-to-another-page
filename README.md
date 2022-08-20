# form-action-of-a-page-to-another-page-in-NEXT.js-React.js

# To Transfer data from Ajij.js to PaySlip.jsv  
## Method-1

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
  return (
    <div>
      <h1>{name}</h1>
      <h1>{email}</h1>
    </div>
  );
};
export default PaySlip;
```  

# Method-2
# Ajij.js

```
import {useState} from 'react';
import {useRouter} from 'next/router'

const preventDefault = f => e => {
  e.preventDefault()
  f(e)
}

export default ({action = '/PaySlip'}) => {
   const router = useRouter()
   const [query, setQuery] = useState('')

   const handleParam = setValue => e => setValue(e.target.value)

   const handleSubmit = preventDefault(() => {
     router.push({
       pathname: action,
       query: {q: query},
     })
   })

   return (
     <form onSubmit={handleSubmit}>
       <input
         type='text'
         name='q'
         value={query}
         onChange={handleParam(setQuery)}
         placeholder='Search'
         aria-label='Search'
       />
     </form>
   )
};
```  

# PaySlip.js

```
import {useRouter} from "next/router";
const PaySlip =() =>{
  const router = useRouter();
  const {name,email} = router.query;
  return (
    <div>
      <h1>{name}</h1>
      <h1>{email}</h1>
    </div>
  );
};
export default PaySlip;
```  





