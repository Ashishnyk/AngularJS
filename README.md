<!DOCTYPE html>
<html>
<head>
    <title>Form validation</title>
    <link rel="stylesheet" href="dist/css/bootstrap.css">
    <link href="dist/js/jquery.min.js">
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
    <script src="validation10.js"></script>

</head>
<body><br>


<div ng-app="validationApp" ng-controller="mainController">
    <div>
        <button ng-click="register()">Register</button>
        <button ng-click="login()">Login</button>
    </div>
    <div class="container">
        <div class="row" ng-show="!showPanel">  
           
            <div class="col-sm-6">
            <!-- FORM ============ -->
          
                <form name="userForm" role="form"  novalidate>

                    <!-- NAME -->
                    <div class="form-group" ng-class="{ 'has-error' : userForm.name.$invalid && !userForm.name.$pristine }">
                        <label>Name</label>
                        <input type="text" name="name" class="form-control" ng-model="formdata.name" required>
                        <p ng-show="userForm.name.$invalid && !userForm.name.$pristine" class="help-block">You name is required.</p>
                    </div>
                  
                    <!-- USERNAME -->
                    <div class="form-group" ng-class="{ 'has-error' : userForm.username.$invalid && !userForm.username.$pristine }">
                        <label>Username</label>
                        <input type="text" name="username" class="form-control" ng-model="formdata.username" ng-minlength="3" ng-maxlength="8">
                        <p ng-show="userForm.username.$error.minlength" class="help-block">Username is too short.</p>
                        <p ng-show="userForm.username.$error.maxlength" class="help-block">Username is too long.</p>
                    </div>
                    
                    <!-- EMAIL -->
                    <div class="form-group" ng-class="{ 'has-error' : userForm.email.$invalid && !userForm.email.$pristine }">
                        <label>Email</label>
                        <input type="email" name="email" class="form-control" ng-model="formdata.email">
                        <p ng-show="userForm.email.$invalid && !userForm.email.$pristine" class="help-block">Enter a valid email.</p>
                    </div>
                    
                    <button ng-show="!showButton" type="submit" class="btn btn-primary" ng-disabled="userForm.$invalid" ng-click="submitForm()">Submit</button>
                    <button ng-show="showButton" type="submit" class="btn btn-primary" ng-disabled="userForm.$invalid" ng-click="updateForm()">Update</button>
                    
                </form>
            </div>

            <table class="table">
                <tr>
                    <th>Name
                    </th>
                    <th>Username
                    </th>
                    <th>Email
                    </th>
                    <th>
                        Edit
                    </th>
                </tr>
                <tr ng-repeat="formdata in formdatas track by $index">
                    <td>{{formdata.name}}</td>
                    <td>{{formdata.username}}</td>
                    <td>{{formdata.email}}</td>
                    <td><button ng-click="editList($index)">Edit</button></td>
                </tr>
            </table>
          
            
        </div>
         <div class="row" ng-show="showPanel"> 
            <form>

                        
                        <div class="form-group" ng-class="{ 'has-error' : userForm.username.$invalid && !userForm.username.$pristine }">
                            <label>Username</label>
                            <input type="text" name="username" class="form-control" ng-model="formdata1.username1" >
                        </div>
                        
                        <!-- EMAIL -->
                        <div class="form-group">
                            <label>Email</label>
                            <input type="email" name="email" class="form-control" ng-model="formdata1.email1">
                        </div>
                        
                        <button ng-show="!showButton" type="submit" class="btn btn-primary" ng-click="signIn(formdata1.username1,formdata1.email1)">Sign In</button>
                    </form>
                    <br>
                    <br>
                    Name:{{userDetail.name}}
                    Email:{{userDetail.email}}
                <div>
    </div>
</div>

</body>
</html>
