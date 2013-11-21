<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html lang="en">
<head>
    <title>Ooyala Test</title>
 
    <script type="text/javascript" src="http://player-staging.ooyala.com/v3/4a71bfa5c2bf45e9b11ee25cb6092f15"></script>
    <script type="text/javascript">
        var vPlayer;
    </script>
</head>
<body >
<div id='playerwrapper' style='width:854px;height:480px;'></div>
<br/><br/>
 
 
 
<div id="logger"></div>
 
 
<script type="text/javascript">
 
     vPlayer = OO.Player.create('playerwrapper', "ZnbjEwNjqXAyAaK0B8EyE8DJw7xA260c", {
 
         /* 'vast': {  //5rbnhkNzrCsum3bOijeXzZlInXDARBAc
             tagUrl: 'http://se.ooyala.com/luke/ads/videoplazavast.xml'
         }, */
 
         'vpaid-ads-manager': {
             adTag: 'http://vast.bp3851706.btrll.com/vast/3851706?n=%n'
             showAdMarquee: false
         },
 
 
        onCreate: function(player) {
        player.mb.subscribe('*','myPage', function(eventName, details) {
 
            if(eventName == "error") alert(vPlayer.getError());
 
            if(eventName == "willPlayAds") {
               document.getElementById('logger').innerHTML += ("will play ads: " + details + "<br/>"); 
            } else if(eventName == "playheadTimeChanged") {
                //document.getElementById('logger').innerHTML += ("Position: " + vPlayer.getPlayheadTime() + "; Duration: " + vPlayer.getDuration() + "<br/>");
            } else if(eventName == "sizeChanged") {
                
            } else if(eventName == "willShowCompanionAds") {
                   document.getElementById('logger').innerHTML += (eventName + "<br/>");
                    for(key in details.ads[0]) {
                        document.getElementById('logger').innerHTML += (key + ": " + details.ads[0][key] + "<br/>");
                    }
            } else if(eventName == "adsPlayed") {
                   document.getElementById('logger').innerHTML += (eventName + "<br/>");
                    vPlayer.destroy();
                
            } else {
                document.getElementById('logger').innerHTML += (eventName + "<br/>");
                if(details) document.getElementById('logger').innerHTML += ("PLUS: " + details + "<br/>");
            }
 
            });
 
 
        },autoplay: false
    });
 
 
</script>
<input type="button" value="play" onclick="vPlayer.play();" />
 
</body>
</html>
