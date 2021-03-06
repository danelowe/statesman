## v0.8.3 2 September 2014
*Fixes*

- Optimisation for Machine#available_events (patch by [@pacso](https://github.com/pacso))

## v0.8.2 2 September 2014
*Fixes*

- Stop generating a default value for the metadata column if using MySQL.

## v0.8.1 19 August 2014
*Fixes*

- Adds check in Machine#transition to make sure the 'to' state is not an empty array (patch by [@barisbalic](https://github.com/barisbalic))

## v0.8.0 29 June 2014
*Additions*

- Events. Machines can now define events as a logical grouping of transitions (patch by [@iurimatias](https://github.com/iurimatias))
- Retries. Individual transitions can be executed with a retry policy by wrapping the method call in a `Machine.retry_conflicts {}` block (patch by [@greysteil](https://github.com/greysteil))

## v0.7.0 25 June 2014
*Additions*

- `Adapters::ActiveRecord` now handles `ActiveRecord::RecordNotUnique` errors explicitly and re-raises with a `Statesman::TransitionConflictError` if it is due to duplicate sort_keys (patch by [@greysteil](https://github.com/greysteil))

## v0.6.1 21 May 2014
*Fixes*
- Fixes an issue where the wrong transition was passed to after_transition callbacks for the second and subsequent transition of a given state machine (patch by [@alan](https://github.com/alan))

## v0.6.0, 19 May 2014
*Additions*
- Generators now handle namespaced classes (patch by [@hrmrebecca](https://github.com/hrmrebecca))

*Changes*
- `Machine#transition_to` now only swallows Statesman generated errors. An exception in your guard or callback will no longer be caught by Statesman (patch by [@paulspringett](https://github.com/paulspringett))

## v0.5.0, 27 March 2014
*Additions*
- Scope methods. Adds a module which can be mixed in to an ActiveRecord model to provide `.in_state` and `.not_in_state` query scopes.
- Adds `Machine#after_initialize` hook (patch by [@att14](https://github.com/att14))

*Fixes*
- Added MongoidTransition to the autoload statements, fixing [#29](https://github.com/gocardless/statesman/issues/29) (patch by [@tomclose](https://github.com/tomclose))

## v0.4.0, 27 February 2014
*Additions*
- Adds after_commit flag to after_transition for callbacks to be executed after the transaction has been
committed on the ActiveRecord adapter. These callbacks will still be executed on non transactional adapters.

## v0.3.0, 20 February 2014
*Additions*
- Adds Machine#allowed_transitions method (patch by [@prikha](https://github.com/prikha))

## v0.2.1, 31 December 2013
*Fixes*
- Don't add attr_accessible to generated transition model if running in Rails 4

## v0.2.0, 16 December 2013
*Additions*
- Adds Ruby 1.9.3 support (patch by [@jakehow](https://github.com/jakehow))
- All Mongo dependent tests are tagged so they can be excluded from test runs

*Changes*
- Specs now crash immediately if Mongo is not running

## v0.1.0, 5 November 2013

*Additions*
- Adds Mongoid adapter and generators (patch by [@dluxemburg](https://github.com/dluxemburg))

*Changes*
- Replaces `config#transition_class` with `Statesman::Adapters::ActiveRecordTransition` mixin. (inspired by [@cjbell88](https://github.com/cjbell88))
- Renames the active record transition generator from `statesman:transition` to `statesman:active_record_transition`.
- Moves to using `require_relative` internally where possible to avoid stomping on application load paths.

## v0.0.1, 28 October 2013.
- Initial release
