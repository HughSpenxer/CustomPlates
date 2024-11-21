# CustomPlates
Random pictures of customized plates.
<!DOCTYPE html>
<html>
<head>
	<title>Broken Hearts Game</title>
	<style>
		/* Add styles here */
	</style>
</head>
<body>
	<div id="game-container">
		<div id="hearts"></div>
		<div id="score">Score: 0</div>
		<div id="time">Time: 60</div>
	</div>

	<script>
		// Game logic here
		let score = 0;
		let time = 60;
		let hearts = [];

		// Create hearts
		for (let i = 0; i < 20; i++) {
			const heart = document.createElement("div");
			heart.className = "heart";
			heart.style.top = Math.random() * window.innerHeight + "px";
			heart.style.left = Math.random() * window.innerWidth + "px";
			document.getElementById("hearts").appendChild(heart);
			hearts.push(heart);
		}

		// Game loop
		setInterval(() => {
			time--;
			document.getElementById("time").innerText = `Time: ${time}`;

			if (time <= 0) {
				alert(`Game over! Your score is ${score}`);
			}

			// Move hearts
			hearts.forEach((heart) => {
				heart.style.top = parseInt(heart.style.top) + 2 + "px";

				if (parseInt(heart.style.top) > window.innerHeight) {
					heart.style.top = "-20px";
					heart.style.left = Math.random() * window.innerWidth + "px";
				}
			});
		}, 1000);

		// Tap to break hearts
		document.addEventListener("click", (e) => {
			const heart = document.elementFromPoint(e.clientX, e.clientY);
			if (heart.classList.contains("heart")) {
				heart.style.display = "none";
				score++;
				document.getElementById("score").innerText = `Score: ${score}`;
			}
		});
	</script>
</body>
</html>