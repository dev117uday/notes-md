# Miscellaneous

## Sending a Request

```java
@Bean
public void SendRequest() throws IOException {
		OkHttpClient client = new OkHttpClient().newBuilder()
				.build();

		String idToken = "eyJhbGciOiJSUzI1NiIsImtpZCI6ImQ0ZTA2Y2ViMjJiMDFiZTU2YzIxM2M5ODU0MGFiNTYzYmZmNWE1OGMiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJhY2NvdW50cy5nb29nbGUuY29tIiwiYXpwIjoiNzM4MTYzMTE5NDU3LTZlb2k0bjVoaWEya2dkbHRzNWdyOWViNXQ5aWxidHRjLmFwcHMuZ29vZ2xldXNlcmNvbnRlbnQuY29tIiwiYXVkIjoiNzM4MTYzMTE5NDU3LTZlb2k0bjVoaWEya2dkbHRzNWdyOWViNXQ5aWxidHRjLmFwcHMuZ29vZ2xldXNlcmNvbnRlbnQuY29tIiwic3ViIjoiMTA1MjMwOTI2NTAzNjg2Njg5NzgxIiwiZW1haWwiOiJ5YWRhdjExN3VkYXlAZ21haWwuY29tIiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImF0X2hhc2giOiIwamdyNUY5WmZ0azJZb2hPX0JyWE9RIiwiaWF0IjoxNjM4MDIxOTA1LCJleHAiOjE2MzgwMjU1MDV9.NMBQ3UpmkUzNeE3mhU29IcszLxZ04lyscpYQzgyuczbYdA3-OJ8qHxUCWkNMPcjitDu9E8KonK8DkwVhJmI0n5TkNAxZkvgxxlhiErQvpGv63s3QldRjTsnvXQw-J_V_OhmOyGLo5JStFu8m90tjrIE-m2f8parrqhz3tb31fhDeLhdHJWcVm2B9l5B9hjz3BpVCf08va0ucC6E9MdE1gWuxc9CyyFi7fzk4TI0B-5-up1inbKVPEXuO2i50SGS1IMM8kLCNREaQth5VLJgHGnkyS_X-5x-gofb7k7raOJs_UibjpdEeQzhFHNUNjAWkdwxNiJcVstpE7M1kCTgztQ";
		String url = "https://www.googleapis.com/oauth2/v3/tokeninfo?id_token=" + idToken;

		System.out.println(url);

		Request request = new Request.Builder()
				.url(url)
				.method("GET", null)
				.build();
		Response response = client.newCall(request).execute();
		System.out.println(response.body().string());

}

// POM.XML

<dependency>
			<groupId>com.squareup.okhttp3</groupId>
			<artifactId>okhttp</artifactId>
			<version>4.1.0</version>
</dependency>
```
