### Optional 主要解决NullpointException

**\*Optional*** **不是** **\*Serializable***。因此，它不应该用作类的字段。**Optional 主要用作返回类型**

- of() 和 ofNullable()

​      of()对象为空时抛出异常 ofNullable()	不会，isPresent()方法执行判空检查

- 返回默认值 orElse()和orElseGet

  ``` java
  /**
  * orElse() 返回默认值时会创建对象
  **/
  public void whenEmptyValue_thenReturnDefault() {
      User user = null;
      User user2 = new User("anna@gmail.com", "1234");
      User result = Optional.ofNullable(user).orElse(user2);
  
      assertEquals(user2.getEmail(), result.getEmail());
  }
  /**
  *orElseGet() 返回默认值时不创建对象
  **/
  User result = Optional.ofNullable(user).orElseGet( () -> user2);
  
  /**
  *orElseThrow() 对象为空时抛出异常
  **/
  public void whenThrowException_thenOk() {
      User result = Optional.ofNullable(user)
        .orElseThrow( () -> new IllegalArgumentException());
  }
  ```


