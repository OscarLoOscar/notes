<dependency>
    <groupId>com.fasterxml.jackson.datatype</groupId>
    <artifactId>jackson-datatype-jsr310</artifactId>
    <version>2.9.7</version>
</dependency>


import com.fasterxml.jackson.databind.DeserializationFeature;
import com.fasterxml.jackson.databind.ObjectMapper;
import com.fasterxml.jackson.databind.SerializationFeature;
import com.fasterxml.jackson.databind.module.SimpleModule;
import com.fasterxml.jackson.databind.ser.std.ToStringSerializer;
import com.fasterxml.jackson.datatype.jsr310.JavaTimeModule;
import org.springframework.context.annotation.Bean;
import org.springframework.stereotype.Component;

```java
@Component
public class JsonObjectMapperConfig {

    @Bean
    public ObjectMapper ObjectMapper(){
        SimpleModule simpleModule = new SimpleModule();
        simpleModule.addSerializer(Long.class, ToStringSerializer.instance);
        simpleModule.addSerializer(Long.TYPE, ToStringSerializer.instance);
        ObjectMapper objectMapper = new ObjectMapper();
        objectMapper.registerModule(simpleModule);
        objectMapper.registerModule(new JavaTimeModule());
        objectMapper.disable(SerializationFeature.WRITE_DATES_AS_TIMESTAMPS);
        objectMapper.configure(DeserializationFeature.FAIL_ON_UNKNOWN_PROPERTIES, false);
        return objectMapper;
    }
}
```


1、ObjectMapper

Jackson ObjectMapper Class(com.fasterxml.jackson.databind.ObjectMapper)是使用Jackson解析JSON最簡單的方法；
Jackson ObjectMapper可以從String、Stream或documents解析JSON，
並創建Java Object來表示已解析的JSON。
將JSON解析為Java對象也稱為從JSON Deserialize to Java Object；
Jackson ObjectMapper也可以從Java對象創建JSON。
從Java對象生成JSON的過程也被稱為Serialize Java Object到JSON；
Jackson Object Mapper 可以把JSON解析為用戶自定義類對象，
或者解析為JSON內置的樹模型的對象；

就是==將JSON與Java對象之間互相轉換==。

2、配置解釋
```java
    @Bean
    public ObjectMapper ObjectMapper(){
        // 可以將各種Module註冊到ObjectMapper中，每個Module中可以包含多個Deserialize組件
        SimpleModule simpleModule = new SimpleModule();
        // 添加將long轉成String的組件
        simpleModule.addSerializer(Long.class, ToStringSerializer.instance);
        simpleModule.addSerializer(Long.TYPE, ToStringSerializer.instance);
        ObjectMapper objectMapper = new ObjectMapper();
        objectMapper.registerModule(simpleModule);
        // 將時間Deserialize組件添加到ObjectMapper中
        objectMapper.registerModule(new JavaTimeModule());
        // 禁止將時間類型數據轉換成時間戳
        objectMapper.disable(SerializationFeature.WRITE_DATES_AS_TIMESTAMPS);
        objectMapper.configure(DeserializationFeature.FAIL_ON_UNKNOWN_PROPERTIES, false);
        return objectMapper;
    }
```