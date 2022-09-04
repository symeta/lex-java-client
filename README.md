# lex-java-client

## Steps of creating a lex java client
1. install AWS JAVA SDK package through IDE
add libraries through maven, key word: aws-java-sdk-lex
<img width="979" alt="Screen Shot 2022-09-04 at 12 11 11 PM" src="https://user-images.githubusercontent.com/97269758/188296989-485460d9-56e8-4b8d-a933-222b14c582e4.png">

2. config smallest authorization privilege of the Java client though IAM
create an IAM user (programmatic access) @ IAM console;

grante the IAM user with the following permissions:
-AmazonLexReadOnly
-AmazonLexRunBotsOnly

configure AK, SK, region @ Java Client Local machine through aws configure command

3. code writing to build a lex java client 
Sample Code of building a lex java client
```java
package io.github.symeta.aws.lex;

import com.amazonaws.regions.Regions;
import com.amazonaws.services.lexruntime.AmazonLexRuntime;
import com.amazonaws.services.lexruntime.AmazonLexRuntimeClientBuilder;
import com.amazonaws.services.lexruntime.model.PostTextRequest;
import com.amazonaws.services.lexruntime.model.PostTextResult;

public class main{
  public static void main (String[] args) {
    AmazonLexRuntime client = AmazonLexRuntimeClientBuilder.standard().withRegion(Regions.US_EAST_1).build();
    PostTextRequest textRequest = new PostTextRequest();
    textRequest.setBotName("BookTrip");
    textRequest.setBotAlias("pre-prod");
    textRequest.setUserId("testuser");
    textRequest.setInputText("");
    PostTextResut textResut = client.postText(textRequest);
    System.out.println(textResult.getDialogState());
    System.out.println(textResult.getMessage());
  }
}
```
detailed SDK api info could be refered to as below:
https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/services/lexruntime/AmazonLexRuntime.html
