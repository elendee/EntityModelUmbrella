# EntityModelUmbrella
EMU - 2 javascript classes for passing objects easily through many forms on both client and server.
Use these 2 abstract classes for the basic needs of handling large amounts of user input very quickly.
The particular focus is on creating generic, unstyled clientside forms.

## client
The client class mainly provides methods for building forms, accepting input, and posting to server.

### `EmuModel.build_form( callback )`
- optional `callback` middleware fired on form submission.
- *The generated form will block the default DOM form submit behavior and fire the Model's `sumbit()` method instead.

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
