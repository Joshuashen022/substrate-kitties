 #Leaning kitten

----

##Step 1

-----

In the `kitten` pallet, originally we have `pallet::Config` as following

```rust
#[pallet::config]
    pub trait Config: frame_system::Config {
        /// Because this pallet emits events, it depends on the runtime's definition of an event.
        type Event: From<Event<Self>> + IsType<<Self as frame_system::Config>::Event>;

        /// The Currency handler for the Kitties pallet.
        type Currency: Currency<Self::AccountId>;

        // TODO Part II: Specify the custom types for our runtime.

    }
```
And in the `runtime`, originally we have `pallet` implementation as
```rust
impl pallet_kitten::Config for Runtime {
	  type Event = Event;
}
```
We can see that `type Curency` is not implemented, so add the following line to it
```rust
impl pallet_kitten::Config for Runtime {
    type Event = Event;
    type Currency = Balances; // <-- Add this line
}
```
