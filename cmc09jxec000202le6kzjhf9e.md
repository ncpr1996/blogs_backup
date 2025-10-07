---
title: "How I Built a Complete 2D Game Using Amazon Q Developer CLI - Beginner's Guide"
datePublished: Tue Jun 17 2025 08:30:44 GMT+0000 (Coordinated Universal Time)
cuid: cmc09jxec000202le6kzjhf9e
slug: how-i-built-a-complete-2d-game-using-amazon-q-developer-cli-beginners-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1750141511231/122c740d-aa07-4aeb-8861-14ae29f45226.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1750142467516/df632f06-997c-402d-9e8f-139d1659af64.png
tags: ai, aws, cloud-computing, game-development, amazon-web-services, ai-tools, amazon-q-developers, amazon-q-developer-cli, amazonqcli

---

I always thought it was impossible to make a game. It felt like there was too much complicated code, programming principles, and technical difficulties. However, I found that creating games is not only possible but enjoyable thanks to AI tools like AmazonQ CLI! Allow me to explain how I made the endless runner game "Tomb Bound" and the lessons I discovered.

## **🎮 Want to see the game in action?**

* **View the GitHub repo**: [https://github.com/ncpr1996/Tomb\_Bound](https://github.com/ncpr1996/Tomb_Bound)
    
* **Explore the code**: Full source code with documentation and setup instructions
    

## Why I Chose an Endless Runner Game

I choose an endless runner since it's straightforward but thrilling. You've played games like Subway Surfers or Temple Run? That's just what I intended to produce. In an attempt to achieve the greatest score, the player sprints automatically and jumps over obstacles.

For a novice like me, this kind of game was ideal because:

* The rules are easy to understand
    
* Players can start playing immediately
    
* It teaches important game programming concepts
    
* You can see progress quickly, which keeps you motivated
    

## My Game Structure and Architecture

Here's how AI and I organized my "Tomb Bound" game files:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750082596942/4a60b309-7f07-4fd4-9bb6-01f408a8967d.png align="center")

**Note**: The GitHub repository includes gameplay screenshots and additional project resources. That's why this project has screenshot and video folders in this snip.

This is how the game operates: The player jumps over traps while running through a tomb. You lose one of your three hearts (health) when you fall into a trap. The game is over if you hit three traps! The game gets faster and you gain a greater score the longer you survive.

Since the **player folder** held all of the various character animations, it was crucial. The game felt much more alive because each action had its own image:

* **Run.png**: Shows the character running (this plays continuously during normal gameplay)
    
* **Jump.png**: Displays when the player presses spacebar to jump over obstacles
    
* **Hurt.png**: Appears briefly when the player hits a trap and loses health
    

I was able to develop a system that seamlessly transitions between animations depending on the game's events once I informed the AI about these various player states.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750141680139/fd04eb9e-4c5a-475d-9fb8-d9c78eac5276.png align="center")

## How I Learned to Talk to AI

"How do I make a game?" was one of the awful inquiries I initially posed to the AI. It didn't work out! I discovered AI need comprehensive data in order to provide accurate responses.

### Bad Prompt:

*"Help me with collision detection."*

### Good Prompt:

*"I'm making a 2D endless runner in Python with Pygame. My player character is 64x64 pixels and can jump. I have trap obstacles that are 32x48 pixels moving from right to left. I need collision detection that takes away one health point when the player touches a trap, but also gives the player a brief moment where they can't get hurt again (so they don't lose all health instantly). How can I do this?"*

The specific query was just what I needed!

### Advanced Prompting Techniques I Discovered

**The Component-Specific Approach**

I discovered that it was better to divide my requests into game components rather than asking for everything at once:

*"I need an audio manager system for my endless runner game. It should handle background music that loops continuously, sound effects for jumping and collisions, volume controls that players can adjust in settings, and graceful error handling if audio files are missing. The system should work with Pygame's mixer and be easy to integrate with my existing game loop."*

**The Visual Effect Prompting Strategy**

**The Integration-Focused Method**

I learnt how to explain the technical specifications as well as the visual objectives for complex structures like the improved title screen:

*"I want to create an impressive main menu title for 'Tomb Bound' that feels like a professional game. The title should have gradient text effects, a glowing animation that pulses, floating particles around the text, and decorative elements like skulls and torches. It needs to integrate smoothly with my existing menu system and update every frame without impacting performance."*

## Amazing Problems AI Solved for Me

### Creating Professional Visual Effects

My request for assistance with decorative elements resulted in one of the most striking solutions. Instead of looking like a simple instructional project, I wanted my game to seem professional.

I prompted: *"I want to create custom decorative graphics for my tomb-themed game - skulls, torches, and scarab beetles. These should be drawn programmatically using Pygame's drawing functions so I don't need external image files. Each decoration should be 60x60 pixels and have appropriate colors and details for an ancient tomb theme."*

The AI produced a comprehensive `create_decorations.py` script within the decorations directory that uses only Python to procedurally produce lovely decorative pieces. This showed me that sometimes you can create exactly what you need without having to search for or purchase visuals!

### Building a Sophisticated Audio System

**Managing game audio seemed incredibly complex, but I described my needs clearly:**

*"I need a centralized audio manager that can handle multiple sound categories (menu sounds, player actions, game events), load audio files from different folders, manage volume levels independently, provide easy on/off toggles for music and sound effects, and handle errors gracefully if files are missing."*

The `audio_manager.py` system that the AI produced was much more advanced than I could have ever dreamed. It had attributes such as:

* Automatic audio file discovery and loading
    
* Categorized sound management (menu, player, game events)
    
* Volume control with real-time adjustment
    
* Graceful fallbacks when audio hardware isn't available
    
* Memory-efficient sound caching
    

### **Implementing Complex Game States**

At first, controlling multiple gaming screens seemed like an impossible task. My game has to manage the settings, credits, pause screen, main menu, gameplay, and game over states.

When I described this challenge: *"My endless runner needs multiple game states that can transition smoothly between each other. Players should be able to pause during gameplay, access settings from both the main menu and pause menu, view scrolling credits, and return to appropriate screens when backing out of menus."*

In order to make transitions logical and manageable, the AI recommended using a clean state machine pattern. More significantly, it described the architectural ideas that enable state management to expand with the complexity of games.

### Creating Spectacular Death Animations

Instead of having the player simply disappear when dying, I wanted something memorable:

*“I need to create a dramatic death sequence for when my player loses all 3 health points after hitting traps. When the player takes their final hit, I want the screen to shake intensely to emphasize the impact, followed by a smooth transition to a professional game over screen. The game over screen should have compelling visual effects and appropriate audio feedback - maybe a dramatic 'game over' sound effect and background music that reflects the defeat. The whole sequence should feel impactful and give players a moment to process their loss before showing restart options.”*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750142055150/92bd1b89-380f-464f-9141-cad2618d2d4b.png align="center")

## Development Automation That Saved Countless Hours

### Procedural Asset Generation

I discovered how to ask the AI for procedural design rather than wasting hours making decorative visuals or looking for free resources:

*"Generate code that creates decorative elements for my tomb-themed game using only Pygame's built-in drawing functions. I need a skull with eye sockets and teeth, a torch with animated flame colors, and an Egyptian scarab beetle with decorative patterns."*

This method offered me the exact style I want while avoiding asset licensing issues.

### Configuration System Generation

Instead of encoding game settings into my codebase, I inquired:

*"Create a JSON-based settings system that can save and load player preferences including audio volume, music on/off toggles, high scores with player names, and any other game configuration. It should handle file errors gracefully and provide sensible defaults."*

The AI produced a comprehensive settings management system that manages error recovery, validation, and persistence automatically.

### Enhanced UI System Creation

Making menus that looked professional seemed impossible until I asked:

*"I need a complete menu system with animated buttons that respond to mouse hover, keyboard navigation support, smooth transitions between menu screens, and professional visual effects like gradients and borders. The system should be extensible for adding new menu options later."*

The outcome was an advanced user interface framework that gave my game a sleek, businesslike vibe.

## Fascinating AI-Generated Solutions

### Dynamic Difficulty Scaling with Player Psychology

I was expecting a straightforward "increase speed over time" approach when I stated that I wanted incremental difficulty. Rather, the AI suggested a system of multifaceted difficulty:

*"The difficulty system should consider not just time survived, but also player performance. Monitor successful jumps, near-misses, and current health to adjust challenge appropriately. Include 'breathing room' periods where difficulty temporarily plateaus, allowing players to experience mastery before facing new challenges."*

This approach showed that AI is capable of taking into account more than just technical implementation; it can also take into account human psychology and game design philosophy.

### Intelligent Collision Detection

The AI offered more than simply simple collision detection. It produced a system with several layers of detection:

* **Broad phase detection** for performance optimization
    
* **Narrow phase detection** for pixel-perfect accuracy
    
* **Collision response gradation** based on impact severity
    
* **Predictive collision** for more responsive feedback
    

### Advanced Animation Systems

The AI recommended frame-based animation solutions for character animations that seamlessly switch between several character states according to the game's setting. Based on damage conditions, landing state, and jump velocity, the system selects animation frames intelligently.

### Professional Visual Polish

The AI recommended adding several "game juice" elements without being specifically asked:

* Screen shake effects when gameover
    
* Particle systems for visual feedback
    
* Smooth scaling and rotation animations
    
* Audio-visual synchronization for maximum impact
    

## The Learning Transformation

### From Implementation to Design Focus

The conventional learning model was reversed when AI was used to help. I could spend weeks understanding Pygame's technical details, then concentrate on creating interesting experiences while letting the AI take care of the complicated implementation.

The AI served as my technical advisor, enabling me to think like a game designer and progressively gain programming knowledge through hands-on practice.

### Understanding Through Iteration

Rapid iteration cycles that would not have been possible with manual implementation were made achievable with AI aid. Instead of days, I could test game design concepts in a matter of hours, which allowed for a great deal of testing and improvement.

### Learning Complex Patterns Through Examples

Instead of learning abstract programming principles, I gained knowledge of them by using them in my own project. In addition to teaching me how to apply solutions, the AI also helped me comprehend why some strategies are more effective than others in particular situations.

## My Development Process with AI

1. **Start with Clear Vision**: I began each feature by clearly describing what I wanted players to experience
    
2. **Break Down Complex Problems**: Large challenges were divided into smaller, specific prompts
    
3. **Iterate and Refine**: Initial solutions were improved through follow-up questions and refinements
    
4. **Test Constantly**: Every AI-generated solution was tested immediately and adjusted as needed
    
5. **Maintain Creative Control**: Technical implementation came from AI, but all creative decisions remained mine
    

## Tips for Other Beginners

### Be Specific with AI Prompts

Don't ask "How do I make a game?" Ask "How do I make my character jump when I press spacebar in a 2D Python game using Pygame, with realistic gravity and ground collision detection?"

### Describe the Player Experience

Describe what you want players to feel and experience rather than technical information. These objectives can be converted into technical solutions by the AI.

### Start Simple, Then Enhance

Use follow-up instructions to add polish and professional features after starting with basic functionality.

### Use Free Resources Strategically

Excellent free assets can be found on websites like Pixabay (audio) and Craftpix (graphics), but when necessary, don't be worried to ask AI to create original stuff.

### Don't Give Up on Complex Features

When you can explicitly explain the desired result to AI, features that appear unattainable become possible.

## The Results

After collaborating with AI, I produced a finished, playable game that included:

* **Smooth character animations** with multiple states (running, jumping, hurt)
    
* **Professional visual effects** including particle systems and screen shake
    
* **Sophisticated audio management** with categorized sounds and volume controls
    
* **Multiple game states** with smooth transitions and professional menus
    
* **Progressive difficulty scaling** that maintains player engagement
    
* **Spectacular death animations** that make failure feel dramatic rather than frustrating
    
* **Persistent high score tracking** with player name storage
    
* **Customizable settings** that save between game sessions
    

Above all, it felt more like a professional game than a learning exercise and was genuinely enjoyable to play!

## Why This Matters for Game Development

The ability to build games is being drastically altered by AI tools such as Amazon Q Developer CLI. Years of studying programming are no longer necessary. You can create it if you can communicate clearly and have a clear vision.

This is not an indication that programming is not useful; on the other hand, it is. However, you can now learn by doing rather than spending months studying theory before producing anything of value.

The goal of game development in the future is to create incredible experiences by fusing human imagination with AI technological know-how, not to replace human creativity with AI.

## What's Next?

I learned while building "Tomb Bound" that anyone who is ready to learn and try new things can become a game developer. While you concentrate on your creativity and design, AI takes care of the technological complexities.

Start by downloading the Amazon Q Developer CLI, coming up with a basic game idea, and then constructing. See what you can make, you might be surprised!

The only question is: what game will you build?

## Conclusion

I learned five important lessons while building "Tomb Bound" with the Amazon Q Developer CLI:

1. **AI makes game development accessible :** Professional game creation no longer requires years of programming study.
    
2. **Clear communication with AI is crucial :** Detailed, precise prompts get far better outcomes than general inquiries.
    
3. **Start simple and build up :** Prioritize the fundamental gameplay before introducing advanced functions and polish.
    
4. **Maintain creative control :** While you make all the creative choices, let AI take care of the technical implementation.
    
5. **Learning by doing works best :** You learn more from building an actual project than from months of theory study.
    

## References

### **Assets and Resources:**

1. [**Craftpix** - 2D Game Assets](https://craftpix.net/)
    
    * Character sprites, backgrounds, traps, and decorations
        
2. [**Pixabay** - Royalty-Free Audio](https://pixabay.com/sound-effects/)
    
    * Sound effects and background music
        

### **Development Tools:**

* **AmazonQ CLI** - AI Development Assistant
    
* **Python -** Programming Language
    
* **Pygame** - Game Development Library
    

## Also Published On

* [AWS Builder Center](https://builder.aws.com/content/33PBKA5u2o5ysMAG4OFrA8zFLEr/how-i-built-a-complete-2d-game-using-amazon-q-developer-cli-beginners-guide)
    
* [Dev Community](https://dev.to/aws-builders/how-i-built-a-complete-2d-game-using-amazon-q-developer-cli-beginners-guide-i4f)