# myTypo_npm_package
npm i myreduxtypes
/////////////////////////////////////////

import { autoTypeGen } from 'myreduxtypes';

example ///
for basic   CRUD 
  const [types, actions] = autoTypeGen('courses');
  
  
  types---->{
  CREATE_FAILED: "CREATE_COURSES_FAILED",
CREATE_START: "CREATE_COURSES_START",
CREATE_SUCCESS: "CREATE_COURSES_SUCCESS",
FIND_FAILED: "FIND_COURSES_FAILED",
FIND_START: "FIND_COURSES_START",
...}

actions---->{
create_failed: function item(data, route),
create_start: function item(data, route),
create_success: function item(data, route),
find_failed: function item(data, route),
find_start: function item(data, route),
...
}

create_start=(data,route)=>({payload: data,
route: route,
type: "CREATE_COURSES_START"

--------------------------------------------------------------------------------------------
if you don't need CRUD operation you can provid more arguments

const [types, actions] = autoTypeGen("user", 'login', 'register')

{
  LOGIN_START: 'LOGIN_USER_START',
  LOGIN_SUCCESS: 'LOGIN_USER_SUCCESS',
  LOGIN_FAILED: 'LOGIN_USER_FAILED',
  LOADING: 'USER_LOADING',
  SET_CURRENT: 'USER_SET_CURRENT',
  REGISTER_START: 'REGISTER_USER_START',
  REGISTER_SUCCESS: 'REGISTER_USER_SUCCESS',
  REGISTER_FAILED: 'REGISTER_USER_FAILED'
}
actions will generate as well like in previos example

-----------------------------------------------------------------------------------------------------
if you provide true as a final argument you will get CRUD operations plus your cusom once


const [types, actions] = autoTypeGen("user", 'login', 'register', true)


////////////////////////////////////////////////////////////////////////////////////////////////////////////
import  {customTypeGen} from  'myreduxtypes';

const [types, actions] = customTypeGen("modal", 'open', 'close')

types would be
{ MODAL_OPEN: 'MODAL_OPEN', MODAL_CLOSE: 'MODAL_CLOSE' }

actiosns
{
modal_close: (data, route)=>({...}),
modal_open:  (data, route)=>({...}),
}

you can provide as much arguments as you wish it will generate all depending first one which is te key

 const [types, actions] = customTypeGen('modal', 'open', 'close', 'toggle');
 {
modal_close: (data, route)=>({...}),
modal_open:  (data, route)=>({...}),
modal_toggle:  (data, route)=>({...}),
}

TYPES===>
 {
 MODAL_CLOSE: "MODAL_CLOSE"
MODAL_OPEN: "MODAL_OPEN"
MODAL_TOGGLE: "MODAL_TOGGLE"
}
