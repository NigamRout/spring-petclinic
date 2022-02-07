
<!DOCTYPE html>
<html lang="en" data-color-mode="auto" data-light-theme="light" data-dark-theme="dark">
  <head>
    <meta charset="utf-8">
  <link rel="dns-prefetch" href="https://github.githubassets.com">
  <link rel="dns-prefetch" href="https://avatars.githubusercontent.com">
  <link rel="dns-prefetch" href="https://github-cloud.s3.amazonaws.com">
  <link rel="dns-prefetch" href="https://user-images.githubusercontent.com/">
  <link rel="preconnect" href="https://github.githubassets.com" crossorigin>
  <link rel="preconnect" href="https://avatars.githubusercontent.com">
  
  <title>spring-petclinic/readme.md at main · NigamRout/spring-petclinic</title>

<div class="clearfix new-discussion-timeline container-xl px-3 px-md-4 px-lg-5">
  <div id="repo-content-pjax-container" class="repository-content " >

<h1 dir="auto">Spring PetClinic Demo for JFrog</h1>

<h2 dir="auto">Introduction</h2>
<p dir="auto">Build a Jenkins PipeLine to build Spring pet-clinic app and bundel and run the app as a docker container</p>

<p><a target="_blank" rel="noopener noreferrer" href="https://github.com/NigamRout/spring-petclinic/blob/main/src/main/resources/static/resources/images/jFrog_Demo.png?raw=true"><img width="1242" alt="petclinic-screenshot" src="https://github.com/NigamRout/spring-petclinic/blob/main/src/main/resources/static/resources/images/jFrog_Demo.png?raw=true" style="max-width: 100%;"></a></p>

<h2 dir="auto">Prerequisites</h2>

<blockquote>
<p dir="auto">Before running the Pet Clinic App, Please make sure you have below Packages in your machine 
  <table>
    <thead>
      <tr> <th> Package Name </th>  <th> Version Used </th>  </tr>
    </thead>
    <tbody>
      <tr> <td> Git </td> <td> 2.16.3 </td> </tr> 
      <tr> <td> Java </td> <td> 1.8.0_191 </td> </tr>
      <tr> <td> Maven </td>  <td> 3 </td>  </tr>
      <tr> <td> Tomcat </td> <td> 8.5 </td> </tr>
      <tr> <td> Docker </td> <td> 19.03.12 </td> </tr>
    </tbody>
  </table>
</p>
</blockquote>


<h2 dir="auto">Steps to SetUp</h2>
<blockquote>
  <h3><p dir="auto">Setting Up Jenkins: </p></h3>
  <ul dir="auto">
    <li>Download jenkins WAR file from (https://www.jenkins.io/download)</li>
    <li>Place the jenkins.war into the <code>webapps</code> folder of Tomcat</li>
    <li>Configure Jenkins with necessary plugins such as Git, Maven, Artifactory</li>
    <li>In Jenkins, Create a pipeline job as mentioned in xyz </li>
  </ul>
</blockquote>

<blockquote>
  <h3><p dir="auto">Setting Up JFrog Artifactory: </p></h3>
  <ul dir="auto">
    <li>Run <code>docker run --name artifactory -d -p 8081:8081 docker.bintray.io/jfrog/artifactory-oss:latest</code> to creat an instance of JFrong Artifactory</li>
    <li>You should be able to access JFrog Artifactory as <code>http://localhost:8081/artifactory</code> </li>
    <li>Go to <code>http://localhost:8081/artifactory/webapp/#/admin/repositories/local</code> to create repos</li>
  </ul>
</blockquote>

<blockquote>
  <h3><p dir="auto">Configure Jenkins PileLine: </p></h3>
  <ul dir="auto">
    <li>In Jenkins create a Pipeline job (let say <i>JFrog_Spring-PetClinic_Build </i>)</li>
    <li>Click on <code>JFrog_Spring-PetClinic_Build</code> </li> 
      <ul dir="auto">
        <li>Go to <code>Pipeline</code> section </li>
        <li>Configure <code>Defination</code> as <code>Pipeline script from SCM</code></li>
        <li>Configure <code>SCM Repository</code> as <code>Git</code></li> 
        <li>Configure <code>Repository URL</code> as <code>https://github.com/NigamRout/spring-petclinic.git</code></li> 
        <li>Configure <code>Repository Branch</code> as <code>*/main</code></li> 
        <li>Configure <code>Script file as </code> as <code>Jenkinsfile</code></li> 
        <li>Finally click on <code>Save</code>
          <p><img width="1175" alt="petclinic-screenshot" src="https://github.com/NigamRout/spring-petclinic/blob/main/src/main/resources/static/resources/images/Jenkins_Job.png?raw=true" style="max-width: 100%;"></p>
        </li>
    </ul>
  </ul>
</blockquote>

<blockquote>
  <h3><p dir="auto">Run and Validate Pipeline:</p></h3>
  <ul dir="auto">
    <li>Go to <code>JFrog_Spring-PetClinic_Build</code> Pipeline job and click on <code>Build Now</code></li>
    <li>You can go to <code>Console Output</code> to check the build logs</li>
    <li>Once build job completed, open URL <code>http://localhost:8082</code> in web browser</li>
  </ul>
</blockquote>

</div>
</readme-toc>
</div>
</div>
</div>

  </div>

  </div>

  </body>
</html>

