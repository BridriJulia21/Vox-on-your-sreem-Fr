# Vox-on-your-sreem-Fr<!DOCTYPE html>
body {
  background: #080808;
}

.tv-demon {
  position: relative;
  width: 200px;
  margin: 120px auto;
}

.screen {
  width: 200px;
  height: 140px;
  border: 5px solid #fff;
  position: relative;
  animation: shake 0.2s infinite;
  background: #111;
  overflow: hidden;
}

.glitch, .glitch2 {
  position: absolute;
  width: 200px;
  height: 140px;
  mix-blend-mode: screen;
  opacity: 0.8;
}

.glitch {
  background: repeating-linear-gradient(
    to bottom,
    #0ff 0px,
    #0ff 4px,
    #111 4px,
    #111 8px
  );
  animation: glitch-move 0.3s infinite;
}

.glitch2 {
  background: repeating-linear-gradient(
    to bottom,
    #f00 0px,
    #f00 3px,
    #111 3px,
    #111 7px
  );
  animation: glitch-move2 0.25s infinite;
}

.body {
  width: 120px;
  height: 200px;
  border: 4px solid white;
  margin: 0 auto;
  margin-top: 10px;
}

@keyframes shake {
  0% { transform: translate(0,0); }
  50% { transform: translate(2px, -2px); }
  100% { transform: translate(-1px, 1px); }
}

@keyframes glitch-move {
  0% { transform: translateY(0); }
  100% { transform: translateY(-10px); }
}

@keyframes glitch-move2 {
  0% { transform: translateY(0); }
  100% { transform: translateY(8px); }
}

</body>
</html>
