# API

FIROS has several REST entry points that can be used to get or post data from/to FIROS.

You can find the old FIROS API [here](https://firos.docs.apiary.io/) (OLD)

## GET /topics

Get topics handled by FIROS with their corresponding _topics_. Each _topic_ contains the `topic`, `messageType`,
`pubsub` and `structure` as follows:

```json
[
    {
        "topic": "/turtle1/cmd_vel",
        "structure": {
            "linear": {
                "y": "float64",
                "x": "float64",
                "z": "float64"
            },
            "angular": {
                "y": "float64",
                "x": "float64",
                "z": "float64"
            }
        },
        "messageType": "geometry_msgs/Twist",
        "pubSub": "subscriber"
    }
]
```

## GET /topic/TOPIC

Gets the data which is published by the topic to e.g the Context-Broker.

Topics, which are retrieved by the Non-ROS-World (`publisher`) are not visible here.

Here as an example for `/topic/turtle1/pose`: the content of `/turtle1/pose`:

```json
{
    "angular_velocity": {
        "type": "number",
        "value": 0.0
    },
    "linear_velocity": {
        "type": "number",
        "value": 0.0
    },
    "theta": {
        "type": "number",
        "value": 0.0
    },
    "y": {
        "type": "number",
        "value": 5.544444561004639
    },
    "x": {
        "type": "number",
        "value": 5.544444561004639
    },
    "type": "turtlesim/Pose",
    "id": "/turtle1/pose"
}
```

## POST /firos

This API handles the subscription data of the context broker.

## POST /connect

This call restores the configuration of FIROS. Disconnected topics are connected again.

## POST /disconnect/NAME

This call forces FIROS to disconnect from the topic specified by the **NAME** parameter. If Publisher, FIROS will no
longer publish its data. If Subscriber, FIROS will not push the Information into the ROS-World
