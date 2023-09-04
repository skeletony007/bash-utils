## `create_object` Function

The `create_object` function is used to create an instance of an object using a
provided object definition file. This function facilitates object instantiation
by handling initialization and configuration tasks. It takes an instance name
and an object definition file as input parameters.

### Parameters

- `instance_name`: A unique name for the instance of the object to be created.
  This name will be used to prefix variables and functions associated with this
  instance.
- `OBJECT_FILE`: The path to the object definition file that contains the
  object's behavior and methods.

### Usage

The `create_object` function allows you to create an instance of an object with
a customized name and behavior defined in the object definition file. This
function automates the process of initializing instance-specific variables and
functions, making it easier to work with object-oriented scripting.

To create an instance of the GitHub object using the `create_object` function,
you can call it as follows:

```bash
create_object my_instance_name MY_OBJECT_FILE
```

### Object Definition File

The object definition file should contain functions and variables specific to
the behavior of the object. The functions within the object definition file are
designed to be used with the created instances and can be customized to define
specific behaviors.

The object definition file should follow the naming convention
`${obj}_function_name` to ensure compatibility with the `create_object`
function. In the provided example, `${obj}` is replaced with the instance name
during object creation.

### Note

- The `create_object` function uses the `sed` command to replace `${obj}`
  placeholders in the object definition file with the actual instance name
  (`instance_name`). This enables customization of variable and function names
  based on the instance.
- If an `init` function is defined within the object definition file, the
  `create_object` function invokes it to perform instance-specific initialization
  tasks.

By using the `create_object` function, you can manage multiple instances of
objects with distinct behaviors while avoiding variable/function conflicts and
automating initialization processes.

### Inheritance

OOP-like "inheritance" may be implemented as follows:

```bash
${obj}_init() {
    ... # Parse child `init` args
    create_object ${obj} parent_object_file parent_init_args
    ... # Rest of child `init` method
}
... # Additional child object methods
```

Defining the new object after the `init` method is evaluated ensures that there
is no conflict between the parent object and the child object init methods.

