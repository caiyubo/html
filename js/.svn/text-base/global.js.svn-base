$(function() {
  //登陆界面调出
  $(".login").on('click', function(event) {
    event.preventDefault();
    /* Act on the event */
    if (checkIn) {
      logOut();
    }else {
      loadHtml("login-box","login",login)
    }
  });
})

//全局变量
var checkIn = false;

//添加<div id=id></div>至body之后---
//id   = 要添加的div的id名字
//url  = include文件夹目录下的html文件名（不包含后缀）
//func = func回调函数
function loadHtml(id,url,func) {
  if (!$("#"+id).length) {
    $("body").append("<div id="+id+" data-load='yes' style='display:none;'></div>");
    $("#"+id).load("include/"+url+".html",function() {
      $(this).find('.sprite-close').on('click',function() {
        $("#"+id).hide();
      });
      func(id);
    }).fadeIn();
  }else {
    $("#"+id).fadeIn();
  }
  $("#"+id).siblings("[data-load]").hide();
}

function login(id) {
  /* Act on the event */
  $("#login").click(function(event) {
    /* Act on the event */
    var mobile = $("#mobile").val();
    var password = $("#password").val();
    $.ajax({
      url: 'api/user/login',
      type: 'GET',
      dataType: 'json',
      data: {
        account: mobile,
        password: password
      },
    })
    .done(function(json) {
      $(".logo").text(mobile);
      $(".login").html("<div class='sprite sprite-quit'></div>"+"退出");
      checkIn = true;
      $("#"+id).hide();
      $("ul.mynav a.checkin").removeClass('displaynone');
    })
    .fail(function() {
      console.log("error");
    })
    .always(function() {
      console.log("complete");
    });
  });
  $("#register").click(function(event) {
    /* Act on the event */
    loadHtml("register-box","register",register)
  });
}

function logOut() {
  $(".login").html("<div class='sprite sprite-quit'></div>"+"登录");
  $(".logo").html("ArtSay");
  $("ul.mynav a.checkin").addClass('displaynone');
  checkIn = false;
}

function setcookie(Cookiename,Cookievalue,Minutes){
  Minutes = parseInt(Minutes);
  var date = new Date();    
  date.setTime(date.getTime() + (Minutes*60*1000));
  $.cookie(Cookiename, Cookievalue,{ path: '/' , expires: date });
}

function register() {

}