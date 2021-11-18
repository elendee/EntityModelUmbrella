# EntityModelUnification
EMU - An ECMA and node class for passing objects easily through many forms on both client and server.  A loose ECS.
Use these 2 abstract classes for the basic needs of handling user input.

## client
The client class mainly provides methods for building forms, accepting input, and posting to server.

### `EmuModel.build_form( callback )`
- optional `callback` on form submission

### `EmuModel.hydrate( type, source, overwrite )`
- enum `type` - 'data' or 'form'
- - data: hydrate from other objects or Models as `source`s
- - form: attempt to hydrate a Model from a given DOM form as `source`, or it's internal form if none is provided.  The form should in turn be created by the Model's `build_form` method to ensure the inputs align with the Model.

### `EmuModel.submit( endpoint, options )`
- post data directly from the model as opposed to from a form element


## server
### `EmuModel.update( upsert )`
- a method for saving or updating, with a togglable `upsert` allowed boolean.

### `EmuModel.publish( private_fields )`
- return all fields marked as public info
- optionally return more private fields where server logic determines it's appropriate
