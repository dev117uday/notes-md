# Observer DP

* Just like subscriber subscribed to a channel on YouTube
* Channel → Subject || Subscriber → Observer
* Observer observes a Subject

#### Subscriber

```java
package org.example;

public class Subscriber {

    private String name;
    private Channel channel = new Channel();

    public Subscriber(String name) {
        this.name = name;
    }

    public void update() {
        System.out.println("video uploaded");
    }

    public void subscriberChannel(Channel ch) {
        this.channel = ch;
    }

}
```

#### Subject

```java
package org.example;

import java.util.ArrayList;
import java.util.List;

public class Channel {

    List<Subscriber> subsLst = new ArrayList<>();
    private String title;

    // add
    public void subscibe(Subscriber sub) {
        subsLst.add(sub);
    }

    public void unsubscriber(Subscriber sub) {
        subsLst.remove(sub);
    }

    public void notifySubscribers() {
        for (Subscriber sub : subsLst) {
            sub.update();
        }
    }

    public void upload(String title) {
        this.title = title;
        notifySubscribers();
    }

}
```

#### Main Code :

```java
Channelch1 = new Channel();

Subscribers1 = new Subscriber("sub 1");
Subscribers2 = new Subscriber("sub 2");
Subscribers3 = new Subscriber("sub 3");

ch1.subscibe(s1);
ch1.subscibe(s2);
ch1.subscibe(s3);

ch1.notifySubscribers();
```
