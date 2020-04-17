# Sodoku-solution-validation-JavaScript
Code wars! Kata Solution.
function validSolution(board) {
	let valid = true;
	const testvaliditiy = (arr) => {
		let set = new Set(arr);
		if (arr.includes(0) || [...set].length !== 9) {
			return false;
		} else {
			return true;
		}
	}
	console.log("row testing ...")
	for (i = 0; i < board.length; i++) {
		if (!valid) break;
		let row = []
		for (j = 0; j < board.length; j++) {
			row.push(board[i][j])
		}
		// console.log(row)
		valid = testvaliditiy(row)
	}

	//column testing
	console.log("Column testing ...")
	for (i = 0; i < board.length; i++) {
		let col = []
		for (j = 0; j < board.length; j++) {
			col.push(board[j][i])
		}
		valid = testvaliditiy(col)
		if (!valid) break;
	}

	//3x3 testing
	console.log("Cube 3x3 testing ...")
	let row = 0;
	let column = 0;
	while (row < 9 && column < 9) {
		let cube = []
		for (i = row; i < row + 3; i++) {
			for (j = column; j < column + 3; j++) {
				cube.push(board[i][j])
			}
		}
		row += 3
		valid = testvaliditiy(cube)
		if (!valid) break;
		if (row == 9 && column != 9) {
			column += 3
			row = 0;
		}
	}
	return valid
}

//test cases:
validSolution([
  [5, 3, 4, 6, 7, 8, 9, 1, 2],
  [6, 7, 2, 1, 9, 5, 3, 4, 8],
  [1, 9, 8, 3, 4, 2, 5, 6, 7],
  [8, 5, 9, 7, 6, 1, 4, 2, 3],
  [4, 2, 6, 8, 5, 3, 7, 9, 1],
  [7, 1, 3, 9, 2, 4, 8, 5, 6],
  [9, 6, 1, 5, 3, 7, 2, 8, 4],
  [2, 8, 7, 4, 1, 9, 6, 3, 5],
  [3, 4, 5, 2, 8, 6, 1, 7, 9]
]); // => true

validSolution([
  [5, 3, 4, 6, 7, 8, 9, 1, 2], 
  [6, 7, 2, 1, 9, 0, 3, 4, 8],
  [1, 0, 0, 3, 4, 2, 5, 6, 0],
  [8, 5, 9, 7, 6, 1, 0, 2, 0],
  [4, 2, 6, 8, 5, 3, 7, 9, 1],
  [7, 1, 3, 9, 2, 4, 8, 5, 6],
  [9, 0, 1, 5, 3, 7, 2, 1, 4],
  [2, 8, 7, 4, 1, 9, 6, 3, 5],
  [3, 0, 0, 4, 8, 1, 1, 7, 9]
]); 
