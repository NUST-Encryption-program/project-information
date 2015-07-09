<!DOCTYPE html>
<html ng-app>
<head lang="en">
    <meta charset="UTF-8">
    <script src="http://apps.bdimg.com/libs/angular.js/1.2.16/angular.min.js"></script>
    <script src="js/controller.js"></script>
    <title>HelloAngularJS</title>
</head>
<body>
    <div ng-controller="HelloController">
	    <p>{{greeting.text}},AngualarJS</p>
    </div>
</body>
</html>

/* controller.js*/
function HelloController($scope){
    $scope.greeting={text:"Hello"}
}
