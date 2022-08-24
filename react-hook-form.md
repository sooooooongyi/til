## react-hook-form 라이브러리

> 맨날 수동으로 사용하던 useform을 라이브러리화 했다구????? 👀
> 

### register

- useform으로 관리하고 싶은 데이터를 등록한다.

```jsx
import React from "react";
import { useForm } from "react-hook-form";

export default function App() {
  const { register, handleSubmit } = useForm();
  const onSubmit = data => console.log(data);
   
  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register("firstName")} />
      <select {...register("gender")}>
        <option value="female">female</option>
        <option value="male">male</option>
        <option value="other">other</option>
      </select>
      <input type="submit" />
    </form>
  )
```

- firstName, gender 라는 key가 등록된다.
- name 속성이 반드시 필요하다.

### 유효성 검사

- required, min, max, minLength, maxLength, pattern, validate

```jsx
import React from "react";
import { useForm } from "react-hook-form";

export default function App() {
  const { register, handleSubmit } = useForm();
  const onSubmit = data => console.log(data);
   
  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register("firstName", { required: true, maxLength: 20 })} />
      <input {...register("lastName", { pattern: /^[A-Za-z]+$/i })} />
      <input type="number" {...register("age", { min: 18, max: 99 })} />
      <input type="submit" />
    </form>
  );
}
```

### 에러 처리

```jsx
import React from "react";
import { useForm } from "react-hook-form";

export default function App() {
  const { register, formState: { errors }, handleSubmit } = useForm();

  const onSubmit = (data) => console.log(data);
  
  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register("firstName", { required: true })} />
      {errors.firstName?.type === 'required' && "First name is required"}
      
      <input {...register("lastName", { required: true })} />
      {errors.lastName && <p>Last name is required</p>}

      <input {...register("mail", { required: "Email Address is required" })} />
      <p>{errors.mail?.message}</p>
      
      <input type="submit" />
    </form>
  );
}
```

- errors.[key이름] 으로 에러를 표현할 수 있다.

### 타입스크립트

```jsx
type FormData = {
  firstName: string;
  lastName: string;
};

...

const { register, setValue, handleSubmit, formState: { errors } } = useForm<FormData>();
```

- 필요한 데이터의 타입을 미리 지정할 수 있다.