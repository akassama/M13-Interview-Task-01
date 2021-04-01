
# .Net Core Version Upgrade
First task of back-end 


### Development Processes for the Tasks (Update .Net Core version from 1.1 to 3.1)
* Update the Target Framework
``` 
<PropertyGroup>
	 <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```


* Removed obsolete package references
``` 
   <ItemGroup>
        <PackageReference Include="HtmlAgilityPack.NetCore" Version="1.5.0.1" />
        <PackageReference Include="Microsoft.ApplicationInsights.AspNetCore" Version="2.0.0" />
        <PackageReference Include="Microsoft.AspNetCore" Version="1.1.1" />
        <PackageReference Include="Microsoft.AspNetCore.Mvc" Version="1.1.2" />
        <PackageReference Include="Microsoft.Extensions.Logging.Debug" Version="1.1.1" />
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
    </ItemGroup>
```

* Update Framework-dependent builds (M13.InterviewProject.runtimeconfig.json)



 	   {
 	   "runtimeOptions": {
            "tfm": "netcoreapp3.1",
            "framework": {
              "name": "Microsoft.NETCore.App",
              "version": "3.1.0"
            },
            "configProperties": {
              "System.GC.Server": true
            }
          }
        }

* Got: “This type is obsolete and will be removed in a future version. The recommended alternative is Microsoft.AspNetCore.Hosting.IWebHostEnvironment.” error.

      
      Updated to IWebHostEnvironment
      Then installed Install-Package HtmlAgilityPack
      Then installed Newtonsoft
      
* Updated program.cs class to

        public class Program
        {
    	    public static void Main(string[] args)
    	    {
    		CreateHostBuilder(args).Build().Run();
    	    }

	        public static IHostBuilder CreateHostBuilder(string[] args) =>
		    Host.CreateDefaultBuilder(args)
			.ConfigureWebHostDefaults(webBuilder =>
			{
				webBuilder.UseStartup<Startup>();
			});
        }

    
    ## Total time took about 1hr
