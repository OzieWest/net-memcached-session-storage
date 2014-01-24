Это форк от  [Memcached Providers project](http://github.com/friism/Memcached-Providers/).

### Open Web.config file and add the following section to configSections tag

```
<sectionGroup name="enyim.com">
	<section name="memcached" type="Enyim.Caching.Configuration.MemcachedClientSection, Enyim.Caching"/>
</sectionGroup>
```

### Add the following section to configure Enyim’s client to point to Memcached servers

```
<enyim.com>
    <memcached>
        <servers>
            <!--put your own server(s) here-->
            <add address="127.0.0.1" port="11211"/> 
        </servers>
        <socketPool minPoolSize="10" maxPoolSize="100" connectionTimeout="00:00:10" deadTimeout="00:02:00"/>
    </memcached>
</enyim.com>
```

### Add the following section to configure Memcached Session State Provider. 

```
<sessionState cookieless="false" regenerateExpiredSessionId="true" mode="Custom"
customProvider="MemcachedSessionProvider">
    <providers>
        <add name="MemcachedSessionProvider"
        type="MemcachedProviders.Session.SessionStateProvider,MemcachedProviders"
        dbType="none"
        writeExceptionsToEventLog="false"/>
    </providers>
</sessionState>
```