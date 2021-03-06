# react-native-clear-cache
react native 清除缓存第三方库
![Mou icon1](/assets/a1.gif)
### 导出方法
- `getCacheSize` - 获取缓存大小
    - `@callBack` - Function - 回调函数
        - `@cacheSize` - String - 缓存大小
        - `@unit` - String - 缓存大小单位(B KB MB G)

# 

- `runClearCache` - 清除缓存
    - `@callBack` - Function - 回调函数

# 

### 使用实例

	import clear from 'react-native-clear-cache';
	
	constructor () {
        super();
        this.state = {
          cacheSize:"",
          unit:"",
        }
        clear.getCacheSize((value,unit)=>{
          this.setState({
            cacheSize:value, //缓存大小
            unit:unit  //缓存单位
          })
        });
        
      }
      
      render() {
        return (
          <View style={{flex: 1,justifyContent: 'center',alignItems: 'center'}}>
            <Text style={{fontSize: 20,textAlign: 'center',margin: 10}}>
              缓存大小{this.state.cacheSize}{this.state.unit}
            </Text>
            <Button title="清除缓存" onPress={this.clearCache.bind(this)}/>
          </View>
        );
      }
      
      clearCache(){
    
        clear.runClearCache(()=>{
    
          console.log("清除成功");
    
        clear.getCacheSize((value,unit)=>{
          this.setState({
            cacheSize:value, //缓存大小
            unit:unit  //缓存单位
          })
        });
          
        });
    
      }
      
      
# 使用方法
## npm i react-native-clear-cache -save

## 自动配置

version>=0.60.0
auto link

version<0.60.0
执行此命令
 react-native link

## 手动配置
#### android配置
1. 设置 `android/setting.gradle`

    ```
    ...
    
    include ':reactNativeClearCache'
    project(':reactNativeClearCache').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-clear-cache/android')
    
    ```

2. 设置 `android/app/build.gradle`

    ```
    ...
    dependencies {
        ...
        compile project(':reactNativeClearCache')
    }
    ```
    
3. 注册模块 (到 MainApplication.java)

    ```
   import com.example.qiepeipei.react_native_clear_cache.ClearCachePackage;
   
    public class MainApplication extends Application implements ReactApplication {
      ......

        @Override
    	protected List<ReactPackage> getPackages() {
      		return Arrays.<ReactPackage>asList(
          			new MainReactPackage(),
          			new new ClearCachePackage()      //<--- 添加
      		);
    	} 

      ......

    }
    ```

### ios配置

`npx pod-install`
