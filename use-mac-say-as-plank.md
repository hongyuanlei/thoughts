## How to use mac tools say as plank

```
#!/bin/bash

function speak
{
  echo $1
  say -v Mei-Jia $1 -r 100
}

function countDown
{
  totalCount=$1
  for (( count=$totalCount; count>=1; count-- ))
  do
    speak $count
  done
}

function work
{
  totalSeconds=$1
  sleep $[totalSeconds-5]
  countDown 5
}

function rest
{
  totalSeconds=$1
  speak "让我们休息${totalSeconds}秒吧..."
  sleep $totalSeconds
}

function prepare
{
  speak "各位老板，开始运动了"
  countDown $1
}

function endSession
{
  speak "你们太牛B了"
}

function startSession
{
  cycles=$1
  workSeconds=$2
  restSeconds=$3
  speak "接下来的运动共${cycles}组，每组${workSeconds}秒，加油，小伙子，小姑娘"
  for (( cycle=1; cycle<=$cycles; cycle++ ))
  do
    speak "现在开始第${cycle}组..."
    work $workSeconds
    rest $restSeconds
  done
}

prepare 5
startSession 8 30 15
endSession
```