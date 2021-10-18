<!DOCTYPE html>

<html>

<head>

<meta charset="ISO-8859-1">

<title>Varsha Singh</title>

<script src="http://ajax.googleapis.com/ajax/libs/angularjs/1.6.6/angular.min.js"></script>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
<script >

var app=angular.module('myApp',[]);

app.controller('myController',function($scope){

 $scope.arrayData=[];

 $scope.arrayData2=[];

 $scope.addData=function(){

  $scope.displayTab=true;

  $scope.arrayData.push($scope.reg);

  $scope.reg=[];

 },

 $scope.updateData=function(updateRow){

  $scope.updateIndex=updateRow;

  $scope.reg=angular.copy($scope.arrayData[updateRow]); 

 }, 

 $scope.updateArray=function(updateRow){

  $scope.arrayData[updateRow]=angular.copy($scope.reg);

  $scope.reg=[];

  $scope.updateIndex=undefined;

 }, 

 $scope.deleteData=function(deleteRow){

  $scope.arrayData.splice(deleteRow,1);

  if($scope.arrayData.length==0)

   $scope.displayTab=false;

 }

})

</script>

</head>

<body ng-app="myApp" ng-controller="myController">

<form action="">

<input type="hidden" ng-model="updateIndex">
<h2 style="text-align: center; color:yellowgreen"> -:FORM PAGE:-</h2>
 <table>

        <tr>

            <td><b>ID</b></td>

            <td>

                <input type="text" class="form-control" id="id" ng-model="reg.id" /></td>

        </tr>

        <tr>

            <td><b>Name</b></td>

            <td>

                <input type="text" class="form-control" id="name" ng-model="reg.name" /></td>

        </tr>

        <tr>

            <td><b>EmailID</b></td>

            <td>

                <input type="text" class="form-control" id="email" ng-model="reg.email" /></td>

        </tr>

        <tr>

            <td><b>Password</b></td>

            <td>

                <input type="password" class="form-control" id="password" ng-model="reg.password" /></td>

        </tr>

        <tr>

            <td><b>Phone</b></td>

            <td>

                <input type="text"  class="form-control" id="phone" ng-model="reg.phone" /></td>

        </tr>

        <tr ng-if="updateIndex==undefined">
c
            <td >

                <input type="button" class="btn btn-success" name="Add" value="Add" ng-click="addData()">

            </td>

        </tr>       

        <tr ng-if="updateIndex>=0">

            <td >

                <button type="button"  class="btn btn-success" ng-click="updateArray(updateIndex)">Update Data</button>

            </td>

        </tr>

    </table>   

     <table class="table table-striped table-bordered bg-light table-hover">       

            <tr>

                <th>ID</th>

                <th>Name</th>

                <th>EmailID</th>

                <th>Password</th>

                <th>Phone</th>

                <th>action</th>

            </tr>     

            <tr ng-repeat="x in arrayData">

                <td ng-bind="x.id" >

                </td>

                <td ng-bind="x.name" >

                </td>

                <td ng-bind="x.email" >

                </td>

                <td ng-bind="x.password" >

                </td>

                 <td ng-bind="x.phone" >

                </td>

                <td>

                <input type="button" class="btn btn-danger" value="update" ng-click="updateData($index)"/>

                <input type="button" class="btn btn-success" value="delete" ng-click="deleteData($index)"/>

                </td>

            </tr>   

    </table>

</form>

</body>

</html>
