
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
  

    
  <div class="clearfix new-discussion-timeline container-xl px-3 px-md-4 px-lg-5">
  <div id="repo-content-pjax-container" class="repository-content " >

<h1 dir="auto">Spring PetClinic Demo for JFrog</h1>

<h2 dir="auto">Table of Content</h2>
<p dir="auto">
    <ul dir="auto">
      <li><a target="_blank" rel="noopener noreferrer" href="#Introduction">Introduction</a></li>
      <li><a target="_blank" rel="noopener noreferrer" href="#Prerequisites">Prerequisites</a></li>
      <li><a target="_blank" rel="noopener noreferrer" href="#SetUpSteps">SetUp Steps</a></li>
      <ol>
        <li><a target="_blank" rel="noopener noreferrer" href="#SetUpJenkins">Setting Up Jenkins</a></li>
        <li><a target="_blank" rel="noopener noreferrer" href="#SetUpJFrog">Setting Up JFrog</a></li>
        <li><a target="_blank" rel="noopener noreferrer" href="#CreatePileLine">Create Jenkins Pipeline</a></li>
        <li><a target="_blank" rel="noopener noreferrer" href="#RunPileLine">Run and Validate Pipeline</a></li>
      </ol>
  </ul>
</p>
</br>

<h2 dir="auto" id="#Introduction">Introduction</h2>
<p dir="auto">Create a Jenkins PipeLine to build Spring pet-clinic app and bundel and run the app as a docker container</p>

<p><a target="_blank" rel="noopener noreferrer" href="https://github.com/NigamRout/spring-petclinic/blob/main/src/main/resources/static/resources/images/jFrog_Demo.png?raw=true"><img width="1242" alt="petclinic-screenshot" src="https://github.com/NigamRout/spring-petclinic/blob/main/src/main/resources/static/resources/images/jFrog_Demo.png?raw=true" style="max-width: 100%;"></a></p>
</br>

<h2 dir="auto" id="#Prerequisites">Prerequisites</h2>
<blockquote>
<p dir="auto">Before running the Pet Clinic App, Please make sure you have below Packages in your machine. I have provided the version info just for reference, you may not need the exact version.   
  <table border="1" width="700">
    <thead>
      <tr> <th width=50%> Package Name </th>  <th width=50%> Version Used </th>  </tr>
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
</br>

<h2 dir="auto" id="SetUpSteps">SetUp Steps</h2>
<blockquote>
  <h3><p dir="auto" id="SetUpJenkins">1. Setting Up Jenkins: </p></h3>
  <ul dir="auto">
    <li>Download jenkins WAR file from (https://www.jenkins.io/download)</li>
    <li>Place the jenkins.war into the <code>webapps</code> folder of Tomcat</li>
    <li>Configure Jenkins with necessary plugins such as Git, Maven, Artifactory</li>
    <li>We will create pipeline job in Jenkins in later step</li>
  </ul>
</blockquote>

<blockquote>
  <h3><p dir="auto" id="SetUpJFrog">2. Setting Up JFrog: </p></h3>
  <ul dir="auto">
    <li>Run <code>docker run --name artifactory -d -p 8081:8081 docker.bintray.io/jfrog/artifactory-oss:latest</code> to creat an instance of JFrong Artifactory</li>
    <li>You should be able to access JFrog Artifactory as <code>http://localhost:8081/artifactory</code> </li>
    <li>Go to <code>http://localhost:8081/artifactory/webapp/#/admin/repositories/local</code> to create repos</li>
  </ul>
</blockquote>

<blockquote>
  <h3><p dir="auto" id="CreatePileLine">3. Create Jenkins PileLine: </p></h3>
  <ul dir="auto">
    <li>In Jenkins create a Pipeline job (let say <i>JFrog_Spring-PetClinic_Build </i>)</li>
    <li>Click on <code>JFrog_Spring-PetClinic_Build</code> </li> 
      <ul dir="auto">
        <li>Go to <code>Pipeline</code> section </li>
        <li>Configure <code>Defination</code> as <code>Pipeline script from SCM</code></li>
        <li>Configure <code>SCM Repository</code> as <code>Git</code></li> 
        <li>Configure <code>Repository URL</code> as <code>https://github.com/NigamRout/spring-petclinic.git</code></li> 
        <li>Configure <code>Repository Branch</code> as <code>*/main</code></li> 
        <li>Configure <code>Script file as </code> as <code>Jenkinsfile</code> and finally click on <code>Save</code> button
          <p><img width="1135" alt="petclinic-screenshot" src="https://github.com/NigamRout/spring-petclinic/blob/main/src/main/resources/static/resources/images/Jenkins_Job.png?raw=true" style="max-width: 100%;"></p>
        </li>
    </ul>
  </ul>
</blockquote>

<blockquote>
  <h3><p dir="auto" id="RunPileLine">4. Run and Validate Pipeline:</p></h3>
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

