Discord.Addons.WebSocketSharp
=============================

This addon adds a websocket provider based on `websocket-sharp`, which
allows Discord.Net to run under Mono, which in turn allows its use on
platforms which .NET Core does not support. Among these is the popular
Raspberry Pi Zero.

Depending on your version of Mono, an additional project-specific workaround may be needed. The `System.Net.Http.dll` file must be deleted from the output directory, and an assembly redirect must be added to the configuration.

```xml
<configuration>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="System.Net.Http" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />
                <bindingRedirect oldVersion="0.0.0.0-4.2.0.0" newVersion="4.0.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
</configuration>
```

```xml
<Target Name="DeleteNetHttpMono" AfterTargets="AfterBuild">
  <Delete Files="$(OutputPath)\System.Net.Http.dll" />
</Target>
```

### Contributing
If you want to contribute, please open an issue on Github and/or contact the authors.

<a href='https://ko-fi.com/H2H176VD' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://az743702.vo.msecnd.net/cdn/kofi2.png?v=0' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>
