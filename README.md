# Baseball Konami Code

:baseball: :video_game: :arrow_up: :arrow_up: :arrow_left: :arrow_right: :arrow_left: :arrow_right: :arrow_down: :arrow_down:

Will a pitcher pitch the Konami Code?

A project for Baseball Hackday 2018 in Boston http://www.baseballhackday.com/boston/.

## Konami Code

The Konami Code (コナミコマンド Konami Komando?, lit. "Konami Command") is a special combination of buttons that appears in several Konami games, including the Contra series. Since it was first revealed, the code has become part of popular culture in general, even appearing in many non-Konami games and diverse media, like clothing, advertisements and non-gaming related software.

The code was first used in the 1986 release of Gradius for the Nintendo Entertainment System but was popularized among North American players in the NES version of Contra, for which it was also dubbed both the "Contra Code" and "30 Lives Code", because of its nearly necessary use in the game.

The Konami Code was created by Kazuhisa Hashimoto, who was developing the home port of the 1985 arcade game Gradius, an horizontal scrolling shooter released on the NES in 1986. Finding the game too difficult to play through during testing, he created a cheat code to give the player a full set of power-ups (normally attained gradually throughout the game). The code was still present in the released version after Hashimoto forgot to remove it. Players discovered and shared the code. The Konami Code was thus included in the series' other sequels and spin-offs.
The code is usually entered during the title screen before the game demo begins, and the player must press the following sequence of buttons on the game controller to enable the cheat:

## UP UP DOWN DOWN LEFT RIGHT LEFT RIGHT A B

Will a pitcher pitch the Konami Code?

Looked at 1.5M pitches from 2017 and 2016 regular season for the pattern `UP UP DOWN DOWN LEFT RIGHT LEFT RIGHT` based on pitch zones.

```
, case
  when b.pitch_zone in ('10', '1', '2', '3') then 'U'
  when b.pitch_zone in ('12', '7', '8', '9') then 'D'
  when b.pitch_zone in ('13', '4') then 'L'
  when b.pitch_zone in ('11', '6') then 'R'
  else
  ''
  end as pitch_kode
```


For simplicity, we ignored the A and B and Start button portion of the code.

It happens only 8 times:

* pitches-mlb-2016-bal-sea-2016-06-30-1910-mlb-joaquin-benoit.json
* pitches-mlb-2016-bos-nyy-2016-09-29-1905-mlb-henry-owens.json
* pitches-mlb-2016-mia-phi-2016-07-18-1905-mlb-fernando-rodney.json
* pitches-mlb-2016-nym-sd-2016-05-6-1940-mlb-ryan-buchter.json
* pitches-mlb-2017-cle-min-2017-08-17-1210-mlb-kyle-gibson.json
* pitches-mlb-2017-hou-tex-2017-06-2-1905-mlb-dillon-gee.json
* pitches-mlb-2017-laa-oak-2017-09-6-1235-mlb-sean-manaea.json
* pitches-mlb-2017-sea-min-2017-06-12-1910-mlb-tony-zych.json
