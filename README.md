# Superdelegate

a [Sails](http://sailsjs.org) application that empowers citizens to contact their nearby superdelegate.

## API

#### `GET` api/v1/superdelegates
Returns all superdelegates. Superdelegate data is updated once daily, and comes from [Wikipedia: List of Democratic Party superdelegates, 2016](https://en.wikipedia.org/wiki/List_of_Democratic_Party_superdelegates,_2016)

##### Success Response
 - **Status** `200`
 - **Content**

    ```json
    [
      {
        "id": "507f191e810c19729de860ea",
        "candidate": "Clinton",
        "delegate": "Alma Adams",
        "group": "Rep.",
        "state": "NC"
      },
      {
        "id": "507f191e810c19729de860ea",
        "candidate": "Clinton",
        "delegate": "Alma Adams",
        "group": "Rep.",
        "state": "NC"
      },
      {
        "id": "507f191e810c19729de860ea",
        "candidate": "Clinton",
        "delegate": "Alma Adams",
        "group": "Rep.",
        "state": "NC"
      }
    ]
    ```

#### `GET` api/v1/superdelegates?state=&delegate=&candidate=&group=

##### Data Params
- **Status** `200`
- **Content**
    The following query parameters are accepted

    | Name | Description |  
    |------|-------------|
    |  state  |  *  | 
    |  delegate  |  *  |
    |  candidate  |  *  |
    |  group  |  *  |


##### Success Response
- **Status** `200`
- **Content**

    ```json
    [
     {
       "id": "507f191e810c19729de860ea",
       "candidate": "Clinton",
       "delegate": "Alma Adams",
       "group": "Rep.",
       "state": "NC"
      }
    ]
    ```

##### Error Response
 - ##### Status Code `422 Unprocessable Entry`

    ```json
    { "error": "Invalid query" }
    ```


#### `POST` api/v1/mail

##### Data Params
- **Status** `200`
- **Content**

    ```json
    {
      "sender_email": "arnold@butchershop.io",
      "sender_name": "Arnold Sandoval",
      "delegate_id": "507f191e810c19729de860ea",
      "is_template_message_modified": false,
      "message": "Dear Ms. Adams ..."
    }
    ```

##### Success Response
- **Status** `200`
- **Content**

    ```json
    {
      "success": "Your message was sent!",
      "timestamp": "2016-03-21T14:30:32+00:00",
      "sender_email": "arnold@butchershop.io",
      "sender_name": "Arnold Sandoval",
      "sender_message": "Dear Ms. Adams ...",
      "delegate": {
        "id": "507f191e810c19729de860ea",
        "candidate": "Clinton",
        "delegate": "Alma Adams",
        "group": "Rep.",
        "state": "NC"
      }
    }
    ```

##### Data Params
- **Status** `422 Unprocessable Entry`
- **Content**

    ```json
    { "error": "Invalid Email" }
    ```
