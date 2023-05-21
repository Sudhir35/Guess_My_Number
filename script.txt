'use strict';

var name = prompt('Enter Your name');
document.getElementById('player').textContent = name;

let number = Math.trunc(Math.random() * 20 + 1);
console.log(number);
let score = 20;
let highscore = 0;

document.getElementById('but2').classList.add('hidden');

const displaymessage = function (message) {
  document.querySelector('.message').textContent = message;
};

document.querySelector('.check').addEventListener('click', function () {
  const guess = Number(document.querySelector('.guess').value);

  if (!guess) {
    displaymessage('Please enter a Number!!!');
  } else if (guess === number) {
    displaymessage('Congratulations');

    document.querySelector('.number').textContent = number;

    document.querySelector('body').style.backgroundColor = '#60b347';

    document.getElementById('but1').classList.add('hidden');

    document.getElementById('but2').classList.remove('hidden');

    if (score > highscore) {
      highscore = score;

      document.querySelector('.highscore').textContent = highscore;
    }
  } else if (guess !== number) {
    if (score > 1) {
      displaymessage(guess > number ? 'High' : 'Low');

      score--;

      document.querySelector('.score').textContent = score;
    } else {
      displaymessage('You Lost the Game!!!');

      document.querySelector('body').style.backgroundColor = 'red';

      document.querySelector('.score').textContent = 0;
    }
  }
});

document.querySelector('.again').addEventListener('click', function () {
  number = Number(Math.trunc(Math.random() * 20 + 1));

  console.log(number);

  score = 20;

  document.querySelector('.score').textContent = score;

  displaymessage('Start guessing...');

  document.querySelector('.number').textContent = '?';

  document.querySelector('.guess').value = '';

  document.querySelector('body').style.backgroundColor = '#222';

  document.querySelector('.number').style.width = '15rem';

  document.getElementById('but1').classList.remove('hidden');

  document.getElementById('but2').classList.add('hidden');
});
