1. XML HTTP Request
All modern browsers support the XMLHttpRequest object to request data from a server.
It works on the oldest browsers as well as on new ones.
It was deprecated in ES6 but is still widely used.

var request = new XMLHttpRequest();
request.open('GET', 'https://api.github.com/users/anuradha9712');
request.send();
request.onload = ()=>{
    console.log(JSON.parse(request.response));
}

2. Fetch
The Fetch API provides an interface for fetching resources (including across the network) in an asynchronous manner.
It returns a Promise
It is an object which contains a single value either a Response or an Error that occurred.
.then() tells the program what to do once Promise is completed.

fetch('https://api.github.com/users/anuradha9712')
.then(response =>{
    return response.json();
}).then(data =>{
    console.log(data);
})

3.  Axios
It is an open-source library for making HTTP requests.
It works on both Browsers and Node js
It can be included in an HTML file by using an external CDN
It also returns promises like fetch API

axios.get('https://api.github.com/users/anuradha9712')
.then(response =>{
    console.log(response.data)
})

question 2. 
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style>
    ul{
        list-style: none;
        line-height: 1.5;
        font-size: 20px;
    }
</style>
<body>
    <div id="getUsers"><h1>getData</h1></div>
    <div id="output">data</div>
</body>
<script>

    document.getElementById('getUsers').addEventListener('click' , getUsers);


function getUsers(){
    fetch('work.json')
    .then((res) => res.json())
    .then((data) => {
        let show =  '<h2> The Data </h2>';
        console.log(data)
        data.forEach(function(user){
            output += `
            
        <ul>
        <li>ID: ${user.id}</li>
        <li>Name: ${user.name}</li>
        <li>Phone:  ${user.phone}</li>
        <li>USERNAME: ${user.username}</li>
        <li>EMAIL: ${user.email}</li>
        <li>WEBSITE:  ${user.website}</li>
        <li>COMPANYNAME: ${user.company.name}</li>
        <li>COMPANYCATCHPHRASE: ${user.company.catchPhrase}</li>
        <li>STREET: ${user.address.street}</li>
        <li>Suite: ${user.address.suite}</li>
        <li>City: ${user.address.city}</li>
        <li>Zipcode:  ${user.address.zipcode}</li>
        <li>lat:  ${user.address.geo.lat}</li>
        <li>lng:  ${user.address.geo.lng}</li>
        </ul>
            
            `;
        }) 
        document.getElementById('output').innerHTML=output
    })
}
</script>
</html>