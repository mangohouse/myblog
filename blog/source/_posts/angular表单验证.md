---
title: angular表单验证规范
date: 2016-10-11 16:49:30
tags: angular
categories: angular
description: angular表单验证规范
---

表单验证规范
    表单验证主要用在信息设置模块，还有渠道管理模块的编辑渠道，新建、编辑分类，组织架构添加、编辑员工，新建编辑部门。
    现在项目中的表单验证有好几种，项目中引入了angular-ui-form-validation.js这个库，但是只有在设置个人信息页里用到了，在渠道管理里面，表单验证
其他的表单验证都是开发人员自己定的，我们需要统一一种验证方式，angular有其自带的一套表单验证规则，可以参考下面的Demo：

Angular 的表单属性 $valid, $invalid, $pristine, $dirty

    Angular 提供了有关表单的属性来帮助我们验证表单. 他们给我们提供了各种有关一个表单及其输入的信息，并且应用到了表单和输入.
    属性类
    描述
    $valid  ng-valid    Boolean 告诉我们这一项当前基于你设定的规则是否验证通过
    $invalid    ng-invalid  Boolean 告诉我们这一项当前基于你设定的规则是否验证未通过
    $pristine   ng-pristine Boolean 如果表单或者输入框没有使用则为True
    $dirty  ng-dirty    Boolean 如果表单或者输入框有使用到则为True
    Angular 也提供了有关表单及其输入框的类，以便你能够依据每一个状态设置其样式.
``` html 

    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8">
                <meta content="IE=edge" http-equiv="X-UA-Compatible">
                    <title>
                    </title>
                    <link href="//cdn.bootcss.com/bootstrap/3.1.1/css/bootstrap.min.css" rel="stylesheet">
                        <style>
                            body
                            {
                                padding-top:30px;
                            }
                        </style>
                     <script src="//cdn.bootcss.com/angular.js/1.5.8/angular.min.js"></script>
        </head>
        <body ng-app="validationApp" ng-controller="mainController">
            <div class="container">
                <div class="col-sm-8 col-sm-offset-2">
                    <div class="page-header">
                        <h1>
                            AngularJS Form Validation
                        </h1>
                    </div>
                    <form name="userForm"  novalidate>
                        <div class="form-group" ng-class="{ 'has-error' : userForm.name.$invalid && !userForm.name.$pristine }">
                            <label>
                                Name
                            </label>
                            <input class="form-control" name="name" ng-model="name" required type="text" ng-model-options="{ updateOn: 'blur' }" />
                            <div class="error" ng-show="userForm.name.$invalid && !userForm.name.$pristine">
                                <p>try again</p>
                            </div>
                        </div>
                        <div class="form-group">
                            <label>
                                Username
                            </label>
                            <input class="form-control" name="username" ng-maxlength="8" ng-minlength="3" ng-model="username" type="text" ng-model-options="{ updateOn: 'blur' }"  required/>
                           <!--  <div class="error" ng-show="">
                                <p>it is required try again</p>
                            </div> -->
                            <div class="error" ng-show="userForm.username.$error.minlength">
                                <p>too short try again</p>
                            </div>
                            <div class="error" ng-show="userForm.username.$error.maxlength ">
                                <p>too long try again</p>
                            </div>
                       </div>
                        <div class="form-group">
                            <label>
                                Email
                            </label>
                            <input class="form-control" name="email" ng-model="email" type="email" ng-model-options="{ updateOn: 'blur' }"  required/>
                            <div class="error" ng-show="userForm.email.$invalid && !userForm.email.$pristine">
                                <p>not a email address</p>
                            </div>
                        </div>
                        <button class="btn btn-primary" type="button" ng-disabled="userForm.$invalid" ng-click="submitForm(userForm.$valid)">
                            Submit
                        </button>
                    </form>
                </div>
            </div>
        </body>
        ``` javascript
        <script type="text/javascript">
            var validationApp = angular.module('validationApp', []);
            validationApp.controller('mainController', function($scope) {

                $scope.submitForm = function(isValid) {

                    if (isValid) {
                        alert('our form is amazing');
                    }
                    else{
                        alert('our form is not amazing');
                    }
                }
                console.log($scope)
            });
        </script>
    </html>
```
相关文章：https://scotch.io/tutorials/angularjs-form-validation，https://docs.angularjs.org/guide/forms#!

