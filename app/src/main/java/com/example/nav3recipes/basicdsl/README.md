# Basic DSL Recipe

This recipe shows a basic example of how to use the Navigation 3 API with two screens, using the `entryProvider` DSL and a persistent back stack.

## How it works

This example is similar to the basic recipe, but with a few key differences:

1.  **Persistent Back Stack**: It uses `rememberNavBackStack(RouteA)` to create and remember the back stack. This makes the back stack persistent across configuration changes (e.g., screen rotation). To use `rememberNavBackStack`, the navigation keys must be serializable, which is why `RouteA` and `RouteB` are annotated with `@Serializable` and implement the `NavKey` interface.

2.  **`entryProvider` DSL**: Instead of a `when` statement, this example uses the `entryProvider` DSL to define the content for each route. The `entry<RouteType>` function is used to associate a route type with its composable content.

The navigation logic remains the same: to navigate from `RouteA` to `RouteB`, we add a `RouteB` instance to the back stack.fun createIncomingCallAttributes(
    callerName: String,
    callerNumber: String,
    isVideoCall: Boolean): CallAttributesCompat {
    val addressUri = Uri.parse("YourAppScheme:$callerNumber")

    // Define capabilities supported by your call.
    val callCapabilities = CallAttributesCompat.CallCapability(
        supportsSetInactive = CallAttributesCompat.SUPPORTS_SET_INACTIVE // Call can be made inactive (implies hold)
    )

    return CallAttributesCompat(
        displayName = callerName,
        address = addressUri,
        direction = CallAttributesCompat.DIRECTION_INCOMING,
        callType = if (isVideoCall) CallAttributesCompat.CALL_TYPE_VIDEO_CALL else CallAttributesCompat.CALL_TYPE_AUDIO_CALL,
        callCapabilitiesCompat = callCapabilities
    )
}
