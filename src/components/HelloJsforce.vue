<template>
  <div class="hello">
    <h1>Hello JSforce</h1>
  </div>
</template>

<script>
import jsforce from "jsforce";
export default {
  name: "HelloJsforce",

  mounted() {
    var conn = new jsforce.Connection({
      oauth2: {
        // you can change loginUrl to connect to sandbox or prerelease env.
        loginUrl: "https://login.salesforce.com/services/oauth2/token",
        clientId:
          "3MVG9kBt168mda_8CDOccrT0FjFjkylM_Njfs_FsxgdKwdDxrzggKVy4atkV8QZAaZDsegSQACw==",
        clientSecret:
          "16490032ACE1C9D23CF013BD3218EBB6532CBA67F6D83B0690B6C75DE4D1D71F",
      },
    });
    conn.login(
      "filippo@moretti.salebox",
      "Matmuret82" + "fmpsGHzbNOqP5nEBMiVU5sfSf",
      (err, userInfo) => {
        if (err) {
          return console.error(err);
        }
        // Now you can get the access token and instance URL information.
        // Save them to establish connection next time.
        console.log(conn.accessToken);
        console.log(conn.instanceUrl);
        // logged in user property
        console.log("User ID: " + userInfo.id);
        console.log("Org ID: " + userInfo.organizationId);
        // ...
      }
    );
  },
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
