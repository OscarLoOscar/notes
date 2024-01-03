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



1、ObjectMapper

Jackson ObjectMapper类(com.fasterxml.jackson.databind.ObjectMapper)是使用Jackson解析JSON最简单的方法；
Jackson ObjectMapper可以从字符串、流或文件解析JSON，并创建Java对象或对象图来表示已解析的JSON。将JSON解析为Java对象也称为从JSON反序列化Java对象；
Jackson ObjectMapper也可以从Java对象创建JSON. 从Java对象生成JSON的过程也被称为序列化Java对象到JSON；
Jackson对象映射器(Object Mapper)可以把JSON解析为用户自定义类对象, 或者解析为JSON内置的树模型的对象；

说白了，就是将json与java对象之间互相转换。

2、配置解释

复制代码
    @Bean
    public ObjectMapper ObjectMapper(){
        // 可以将各种Module注册到ObjectMapper中，每个Module中可以包含多个反序列化组件
        SimpleModule simpleModule = new SimpleModule();
        // 添加将long转成String的组件
        simpleModule.addSerializer(Long.class, ToStringSerializer.instance);
        simpleModule.addSerializer(Long.TYPE, ToStringSerializer.instance);
        ObjectMapper objectMapper = new ObjectMapper();
        objectMapper.registerModule(simpleModule);
        // 将时间反序列化组件添加到ObjectMapper中
        objectMapper.registerModule(new JavaTimeModule());
        // 禁止将时间类型数据转换成时间戳
        objectMapper.disable(SerializationFeature.WRITE_DATES_AS_TIMESTAMPS);
        objectMapper.configure(DeserializationFeature.FAIL_ON_UNKNOWN_PROPERTIES, false);
        return objectMapper;
    }