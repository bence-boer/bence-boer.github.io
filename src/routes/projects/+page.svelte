<script>
  import Carousel from "$lib/components/Carousel.svelte";

  import bird_game_ducking from "$lib/images/bird-game/bird-game-ducking.jpg";
  import bird_game_jump from "$lib/images/bird-game/bird-game-jump.jpg";
  import bird_game_run from "$lib/images/bird-game/bird-game-run.jpg";
  import bird_game_scoreboard from "$lib/images/bird-game/bird-game-scoreboard.jpg";
  import bird_game_start from "$lib/images/bird-game/bird-game-start.jpg";

  const bird_game_images = [
    bird_game_start,
    bird_game_ducking,
    bird_game_jump,
    bird_game_run,
    bird_game_scoreboard
  ];

  import space_battle_bullet from "$lib/images/space-battle/space-battle-bullet.jpg";
  import space_battle_double from "$lib/images/space-battle/space-battle-double.jpg";
  import space_battle_main_screen from "$lib/images/space-battle/space-battle-main-screen.jpg";
  import space_battle_scoreboard from "$lib/images/space-battle/space-battle-scoreboard.jpg";
  import space_battle_shield from "$lib/images/space-battle/space-battle-shield.jpg";
  import space_battle_shooter from "$lib/images/space-battle/space-battle-shooter.jpg";
  import space_battle_upgrade from "$lib/images/space-battle/space-battle-upgrade.jpg";

  const space_battle_images = [
    space_battle_main_screen,
    space_battle_double,
    space_battle_shield,
    space_battle_shooter,
    space_battle_upgrade,
    space_battle_bullet,
    space_battle_scoreboard
  ];
</script>

<h1>Projects</h1>

<p style="color: #8a8a8a; font-style: italic">
  Below you can find some of my favorite hobby projects I've worked on in my free time.
  <br>
  I've also included links to download the Android APKs for the games.
</p>

<section>
  <h2>Space Battle – A Journey Through the Stars!</h2>
  <Carousel media={space_battle_images} />
  <p>Embark on an adventure across the cosmos with "Space Battle," a delightful space shooter game filled with engaging
    challenges and carefully hand-drawn pixel art. Designed to be both fun and visually captivating, "Space Battle"
    invites players of all skill levels to explore, fight, and adapt in a universe filled with various types of
    enemies.</p>

  <h3>Features:</h3>
  <ul>
    <li>🚀 <strong>Varied Gameplay:</strong> Encounter different enemies, each with their own behaviors, offering a
      continuously fresh and enjoyable experience.
    </li>
    <li>🔧 <strong>Power-Ups:</strong> Enhance your spaceship with cannon upgrades for increased firepower, shields for
      protection, shockwave bombs to clear enemies, and healing to repair your vessel.
    </li>
    <li>🎨 <strong>Handcrafted Pixel Art:</strong> Every visual aspect of "Space Battle" has been lovingly created by
      hand, providing a charming and nostalgic visual experience.
    </li>
    <li>🎖️ <strong>Challenging Levels:</strong> Progress through levels that offer a balanced challenge, allowing
      players to gradually build their skills and tackle more complex scenarios.
    </li>
    <li>🎮 <strong>Intuitive Controls:</strong> Easily accessible controls make it simple to pick up and play, regardless
      of your experience with space shooter games.
    </li>
    <li>🏆 <strong>Leaderboards:</strong> Track your progress and achievements, offering additional incentives to replay
      and master the game.
    </li>
  </ul>

  <p>"Space Battle" is not just a game, but an expression of creativity and a celebration of classic gaming themes.
    Whether you're looking to reminisce about retro games or discover something new, "Space Battle" offers a unique and
    engaging experience that players of all ages can enjoy.</p>

  <a href="/apks/SpaceBattle.apk" download="SpaceBattle.apk">
    <button>Download Space Battle</button>
  </a>
</section>

<section>
  <h2>Bird Game – A Desert Adventure Awaits!</h2>
  <Carousel media={bird_game_images} />

  <p>Take flight with "Bird Game," a charming and engaging extended version of the beloved chrome dinosaur game, now
    with a delightful avian twist. Navigate a whimsical pixel-art desert, guiding a cute little bird on a journey filled
    with obstacles and fun.</p>

  <h3>Features:</h3>
  <ul>
    <li>🐦 <strong>Adorable Protagonist:</strong> Control a lovable bird as it runs through the desert, portraying a
      world brought to life with custom pixel art.
    </li>
    <li>🌵 <strong>Dynamic Obstacles:</strong> Dodge cactuses, clouds, and tumbleweeds by jumping, ducking, sliding, and
      diving. Every obstacle offers a new challenge to overcome.
    </li>
    <li>🎨 <strong>Custom-Designed Pixel Art:</strong> Experience a handcrafted visual feast, with every element drawn to
      create an endearing and lively setting.
    </li>
    <li>🕹️ <strong>Accessible Controls:</strong> User-friendly controls make the game enjoyable for all, whether you're
      a novice or an experienced gamer.
    </li>
    <li>🏜️ <strong>Desert Landscape:</strong> The desert setting adds a refreshing backdrop to the classic gameplay,
      enriching the experience with its unique ambiance.
    </li>
    <li>🏅 <strong>Personal Best Tracking:</strong> Strive to beat your own records, adding replay value and a personal
      challenge to every run.
    </li>
  </ul>

  <p>"Bird Game" invites players into a desert world that is as enchanting as it is challenging. With its adorable
    protagonist and carefully designed pixel art, it captures the essence of simple joy and offers a delightful escape
    that can be enjoyed time and again. Explore the desert, evade obstacles, and enjoy the journey with "Bird Game"
    today!</p>

  <a href="/apks/BirdGame.apk" download="BirdGame.apk">
    <button>Download Bird Game</button>
  </a>
</section>

<style lang="scss">
  @use "$lib/styles/colors" as colors;
  @use "$lib/styles/sizes" as sizes;

  button {
    margin: 1em 0;
    display: block;
    padding: 1rem 2rem;
    border-radius: 0.5rem;
    border: none;
    background-color: colors.$accent;
    color: colors.$neutral-light;
    font-size: 1.5rem;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.2s ease-in-out;

    &:hover {
      background-color: colors.$accent-dark;
    }
  }

  li {
    margin: 0.5rem 0;
  }
</style>