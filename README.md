# Smart-Circular-Playlist-Navigation
Problem Statement  You are building a music streaming application. The playlist behaves like a circular list — meaning when the last song finishes, the next song becomes the first song again.

You are developing a music streaming playlist system. The playlist behaves like a circular array:

If the last song finishes → it goes back to the first song.

If we move backward from the first song → it goes to the last song.

You are given:

An array songs representing song IDs.

A list of commands.

Commands can be:

Command	Description
NEXT	move to next song
PREV	move to previous song
PLAY k	jump k steps forward

Return the final song ID after executing all commands.

📥 Example Input
songs = [10,20,30,40,50]

commands = [
"NEXT",
"NEXT",
"PLAY 3",
"PREV"
]
📤 Output
50
🧾 Explanation

Start at index 0 → song = 10

Step	Command	Index	Song
1	NEXT	1	20
2	NEXT	2	30
3	PLAY 3	(2+3)%5 = 0	10
4	PREV	(0-1+5)%5 = 4	50

Final answer → 50

💡 Approach

This is a circular array simulation problem.

We maintain a variable:

currentIndex

To move inside a circular array we use modulo arithmetic.

Move Forward
index = (index + step) % n
Move Backward
index = (index - step + n) % n

This prevents negative indexes.

🧠 Algorithm

Start at index = 0

Iterate through each command

If command = "NEXT"

index = (index + 1) % n

If command = "PREV"

index = (index - 1 + n) % n

If command = "PLAY k"

Extract k

index = (index + k) % n

Return songs[index]
