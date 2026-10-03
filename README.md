# Santa's Elf Strike

Christmas ten-pin bowling in the spirit of the late-90s office classic. Santa (or
Mrs. Claus) bowls a candy-cane ball at a rack of ten wisecracking elves. They
heckle him, they go flying when you hit them, and they complain about it
afterwards. One self-contained HTML file with no build step. The only network
request is for the Press Start 2P font from Google Fonts. Offline, it falls back
to a system monospace font.

The elves, their names and every joke are original. Santa, Mrs. Claus and elves
are folklore, and the music is public domain.

## Deploy

Settings -> Pages -> Deploy from a branch -> main -> / (root). Then open the URL in
Chrome on the phone and use the menu to Add to Home screen. The installed app
opens full screen in landscape.

Everything is relative-pathed, so a project subdirectory works.

## Playing

Each ball takes four steps:

1. **Step** — move Santa left or right along the foul line.
2. **Aim** — the dotted line sweeps. Lock it when it points where you want.
3. **Power** — the bar on the right fills and drains. Harder balls hit harder.
4. **Curve** — the needle swings left and right. Off-centre makes the ball hook
   in the back half of the lane, which is the way to find the pocket.

| Action             | Keyboard              | Touch                     |
|--------------------|-----------------------|---------------------------|
| Step left / right  | ← → or A D            | ◀ ▶, or drag on the lane  |
| Aim, power, curve  | Space, Enter or ↑     | BOWL, or tap the lane     |
| Music and sound    | M (music + sound, sound only, quiet) | ♪          |

Full ten-pin scoring is used: strikes, spares and a 10th-frame bonus, shown on a
real scoresheet. Two-player mode is Santa vs. Mrs. Claus, taking turns frame by
frame. The best score is kept in localStorage.

## How it works

- The lane is simulated top-down in real dimensions: an 18.29 m lane, a 1.05 m
  width, a 21.6 cm ball and pins on a 30.5 cm triangle. Circle collisions use
  masses for the ball and the elves.
- An elf falls when it is pushed or hit hard enough. A fallen elf sweeps the
  elves beside it, so pocket hits carry the rack and head-on hits often leave
  splits. In testing, well-aimed balls strike about a third of the time and
  average around 8½ elves.
- The view is a perspective projection. The pin deck tilts up a little, like a
  stage, so you can always see which elves are left for the spare.
- The music is Jingle Bells and We Wish You a Merry Christmas as PC-speaker
  chiptune, with sleigh-bell ticks, played through Web Audio.

## Updating

Edit, bump `CACHE` in `sw.js`, push. Without the version bump the phone keeps
serving the cached copy.
