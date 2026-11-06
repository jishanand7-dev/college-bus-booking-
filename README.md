# college-bus-booking-

<!DOCTYPE html>
<html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>REC Transport · Bronze and Time</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Italiana&family=Outfit:wght@300;400;600&display=swap');
*{margin:0;padding:0;box-sizing:border-box;user-select:none}
html,body{width:100%;height:100%;background:#000;overflow:hidden;overscroll-behavior:none}
body{font-family:'Outfit',sans-serif;color:#fff;cursor:none}
*{cursor:none!important}::-webkit-scrollbar{display:none;width:0}
@media (hover:none){body,*{cursor:auto!important}.cursor-inner,.cursor-outer{display:none}}
#webgl{position:fixed;inset:0;width:100%;height:100%;z-index:1;outline:none}
.cursor-inner{position:fixed;top:0;left:0;width:6px;height:6px;border:2px solid #fff;border-radius:50%;transform:translate(-50%,-50%);pointer-events:none;z-index:9999}
.cursor-outer{position:fixed;top:0;left:0;width:40px;height:40px;border:1.5px solid rgba(255,255,255,.7);border-radius:50%;transform:translate(-50%,-50%);pointer-events:none;z-index:9998}
.cinematic-container{position:fixed;inset:0;z-index:10;pointer-events:none;display:flex;flex-direction:column;justify-content:space-between;padding:0 60px 40px;}
.main-header{display:flex;justify-content:space-between;align-items:center;width:100%;z-index:20;pointer-events:auto;padding:20px 0}
.brand{font-size:14px;font-weight:600;letter-spacing:5px;text-transform:uppercase}
.header-nav{display:flex;align-items:center;gap:24px}
.nav-link{color:#fff;text-decoration:none;font-size:10px;text-transform:uppercase;letter-spacing:2px;font-weight:500}
.nav-dot{width:3px;height:3px;background:rgba(255,255,255,.2);border-radius:50%}
.contact-btn{display:inline-flex;align-items:center;gap:8px;padding:10px 24px;background:#fff;color:#000;text-decoration:none;font-size:10px;text-transform:uppercase;letter-spacing:1px;font-weight:600;border-radius:20px;transition:transform .3s,background .3s}
.btn-circle{display:inline-block;width:6px;height:6px;border:1px solid #000;border-radius:50%}
.contact-btn:hover{filter:brightness(.92)}
.slide{position:absolute;bottom:12%;pointer-events:none}
#slide-1{left:0;width:100%}#slide-1 .slide-title{margin-left:60px}
#slide-1 .desc-row{position:relative;display:flex;width:100%}
#slide-1 .col-1{margin-left:60px;width:calc(25vw - 60px);max-width:calc(25vw - 60px)}
#slide-1 .col-2{position:absolute;left:calc(25vw + 40px);width:calc(25vw - 60px);max-width:calc(25vw - 60px)}
#slide-2{left:0;width:100%}
#slide-2 .slide-title{margin-left:calc(25vw + 40px)}
#slide-2 .slide-desc{margin-left:calc(50vw + 20px);width:calc(25vw - 60px);max-width:calc(25vw - 60px)}
#slide-2-img{position:fixed;top:90px;left:60px;width:calc(25vw - 60px);aspect-ratio:1/1;overflow:hidden;z-index:2;pointer-events:none;clip-path:inset(0 0 100% 0);transition:clip-path 1.8s cubic-bezier(.16,1,.3,1),opacity .8s ease;opacity:0;background:#0b0614;border:1px solid rgba(255,255,255,.12);padding:6%}
#slide-2-img .seats{width:100%;height:100%;display:grid;grid-template-columns:repeat(4,1fr);gap:5%;transform:scale(1.15);transition:transform 1.8s cubic-bezier(.16,1,.3,1)}
#slide-2-img.active{clip-path:inset(0);opacity:1}#slide-2-img.active .seats{transform:scale(1)}
.seat{border-radius:3px;border:1px solid rgba(255,255,255,.18)}.seat.t{background:#2a1740;border-color:#4b2b78}.seat.y{background:#a855f7;border-color:#c084fc}
#slide-3{left:calc(50vw + 20px);width:calc(25vw - 60px);max-width:calc(25vw - 60px)}
#slide-3 .slide-title{white-space:nowrap}
#slide-4{left:calc(25% + 40px);max-width:600px}
.slide-title{font-family:'Italiana',serif;font-size:116px;line-height:1;font-weight:400;letter-spacing:2px;margin-bottom:20px;color:#f5eaff}
.slide-desc{font-size:16px;line-height:1.7;font-weight:300;color:#d1d5db;letter-spacing:.5px;opacity:0;transform:translateY(30px);transition:opacity .8s cubic-bezier(.25,1,.5,1),transform .8s cubic-bezier(.25,1,.5,1);transition-delay:.4s}
.slide.active .slide-desc{opacity:1;transform:none}
.cta{display:inline-block;margin-top:24px;opacity:0;transition:opacity .8s .7s}
.slide.active .cta{opacity:1}
.slide-title .char{display:inline-block;opacity:0;transform:translateY(50px);filter:blur(12px);transition:opacity .8s cubic-bezier(.25,1,.5,1),transform .8s cubic-bezier(.25,1,.5,1),filter .8s cubic-bezier(.25,1,.5,1)}
.slide.active .slide-title .char{opacity:1;transform:none;filter:blur(0)}
.slide.active{pointer-events:auto}
.story-dashes{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);display:flex;flex-direction:column;gap:12px}
.story-dash{width:2px;height:40px;background:rgba(255,255,255,.15);border-radius:2px}
.story-dash-fill{width:100%;height:0;background:#fff;border-radius:2px}
.grid-horizontal-line{position:fixed;top:70px;left:0;right:0;height:1px;background:rgba(255,255,255,.12);z-index:5;pointer-events:none}
.grid-lines{position:fixed;top:0;left:40px;right:40px;width:calc(100% - 80px);height:100vh;display:flex;justify-content:space-between;z-index:5;pointer-events:none}
.grid-line{position:relative;width:1px;height:100%;background:rgba(255,255,255,.12)}
.grid-line:nth-child(3){margin-top:70px;height:calc(100vh - 70px)}
.grid-dot{position:absolute;left:50%;transform:translate(-50%,-50%);width:6px;height:6px;border-radius:50%;background:rgba(255,255,255,.35);box-shadow:0 0 4px rgba(255,255,255,.15)}
@media (max-width:900px){
 .cinematic-container{padding:0 20px 30px}.header-nav,.grid-lines,.grid-horizontal-line,#slide-2-img{display:none}
 .slide-title{font-size:clamp(44px,13vw,80px)}.brand{letter-spacing:2px;font-size:12px}.contact-btn{padding:10px 14px}
 .slide,#slide-1,#slide-2,#slide-3,#slide-4{left:20px!important;right:20px;width:auto!important;max-width:none!important}
 #slide-1 .slide-title,#slide-2 .slide-title{margin-left:0}#slide-1 .col-1,#slide-2 .slide-desc{margin-left:0;width:auto;max-width:none}
 #slide-1 .col-2{display:none}#slide-3 .slide-title{white-space:normal}
}
body.nogl{background:radial-gradient(120% 80% at 70% 20%,#3b1670 0%,#14072b 45%,#000 100%)}
