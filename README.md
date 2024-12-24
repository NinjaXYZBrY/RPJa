<html lang="en">
<head>
  <base href="/your-repository-name/">
  <meta name="github-pages-repository" content="your-repository-name">
  <meta name="github-pages-branch" content="gh-pages">
  <title>RPG Online - Adventure</title>
  <style>
    /* Previous styles remain unchanged */
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
      background: #1a1a2e;
      color: #fff;
    }

    .container {
      max-width: 800px;
      margin: 0 auto;
    }

    .login-form, .game-ui, .admin-panel {
      background: #16213e;
      padding: 20px;
      border-radius: 8px;
      margin: 10px 0;
    }

    .character {
      display: flex;
      gap: 20px;
      align-items: center;
      background: #0f3460;
      padding: 15px;
      border-radius: 8px;
      margin: 10px 0;
    }

    .stats {
      flex: 1;
    }

    button {
      background: #e94560;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 4px;
      cursor: pointer;
      transition: 0.3s;
      margin: 5px;
    }

    button:hover {
      background: #ff2e63;
    }

    input, select {
      padding: 8px;
      margin: 5px;
      border-radius: 4px;
      border: 1px solid #333;
    }

    .hidden {
      display: none;
    }

    .enemy {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: #532e3f;
      padding: 10px;
      margin: 5px 0;
      border-radius: 4px;
    }

    .edit-enemy-btn {
      background: #4A90E2;
      padding: 5px 10px;
      font-size: 12px;
    }

    .battle-log {
      background: #0a192f;
      padding: 10px;
      height: 150px;
      overflow-y: auto;
      margin: 10px 0;
    }

    .attacks {
      display: flex;
      flex-wrap: wrap;
      gap: 5px;
      margin: 10px 0;
    }

    .attacks button {
      background: #4A90E2;
    }

    .attacks button:disabled {
      background: #666;
      cursor: not-allowed;
    }

    .inventory-container {
      display: flex;
      gap: 20px;
      margin: 10px 0;
    }

    .inventory, .equipped {
      flex: 1;
      background: #16213e;
      padding: 15px;
      border-radius: 8px;
    }

    .item, .equipped-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 5px;
      margin: 5px 0;
      background: #1a1a2e;
      border-radius: 4px;
    }

    .item button, .equipped-item button {
      padding: 5px 10px;
      font-size: 12px;
      margin-left: 5px;
    }

    /* Add element-specific colors */
    .element-water { color: #4FC3F7; }
    .element-fire { color: #FF5722; }
    .element-grass { color: #4CAF50; }
    .element-light { color: #FFD700; }
    .element-dark { color: #424242; }
    .element-shadow { color: #673AB7; }
    .element-space { color: #3F51B5; }
    .element-ice { color: #B3E5FC; }
    .element-earth { color: #795548; }

    /* Add item class styles */
    .class-warrior { color: #ff4d4d; }  
    .class-mage { color: #4d4dff; }
    .class-archer { color: #9966ff; }
    .class-any { color: #cccccc; }

    .enemy-drop {
      margin: 10px 0;
      padding: 5px;
      background: #1f2937;
      border-radius: 4px;
      display: flex;
      gap: 10px;
      align-items: center;
    }

    .enemy-drop select, 
    .enemy-drop input {
      padding: 5px;
      border-radius: 4px;
    }

    .enemy-drop button {
      padding: 5px 10px;
      font-size: 12px;
    }

    .modes {
      display: flex;
      flex-wrap: wrap;
      gap: 5px;
      margin: 10px 0;
    }

    .modes button {
      background: #4A90E2;
      flex: 1;
      min-width: 150px;
      text-align: center;
      padding: 10px;
    }

    .modes button.active {
      background: #2ECC71;
    }

    .modes button:disabled {
      background: #666;
      cursor: not-allowed;
    }

    .crafting {
      background: #16213e;
      padding: 15px;
      border-radius: 8px;
      margin: 10px 0;
    }

    .recipe {
      background: #1a1a2e;
      padding: 10px;
      margin: 5px 0;
      border-radius: 4px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .recipe-materials {
      font-size: 0.9em;
      color: #aaa;
      margin-top: 5px;
    }

    .recipe button {
      background: #4A90E2;
      padding: 5px 10px;
      font-size: 12px;
    }

    .recipe button:disabled {
      background: #666;
      cursor: not-allowed;
    }

    .recipe-material {
      display: flex;
      gap: 10px;
      margin: 5px 0;
      align-items: center;
    }

    .recipe-material select,
    .recipe-material input {
      padding: 5px;
      border-radius: 4px;
    }

    .recipe-material button {
      padding: 5px 10px;
      font-size: 12px;
    }

    .item span {
      font-size: 1em;
      color: #fff;
    }

    /* New styles */
    .inventory-page {
      display: none;
      background: #16213e;
      padding: 20px;
      border-radius: 8px;
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      z-index: 100;
    }

    .inventory-page.active {
      display: block;
    }

    .back-button {
      background: #4A90E2;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 4px;
      margin-bottom: 20px;
      cursor: pointer;
    }

    /* Add styles for explore page */
    .explore-page {
      display: none;
      background: #16213e;
      padding: 20px;
      border-radius: 8px;
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      z-index: 100;
    }

    .explore-page.active {
      display: block;
    }

    .location-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 20px;
      margin-top: 20px;
    }

    .location-card {
      background: #1a1a2e;
      padding: 15px;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.3s;
    }

    .location-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
    }

    .location-card h3 {
      margin-top: 0;
    }

    .location-card p {
      margin: 5px 0;
      font-size: 0.9em;
      color: #aaa;
    }
    
    .guild-chat {
      background: #16213e;
      padding: 20px;
      border-radius: 8px;
      margin-top: 20px;
      display: none;
    }

    .guild-chat.visible {
      display: block;
    }

    .chat-messages {
      height: 300px;
      overflow-y: auto;
      background: #1a1a2e;
      padding: 10px;
      border-radius: 4px;
      margin-bottom: 10px;
    }

    .chat-input {
      display: flex;
      gap: 10px;
    }

    .chat-input input {
      flex: 1;
      padding: 10px;
      border-radius: 4px;
      border: 1px solid #333;
      background: #1a1a2e;
      color: white;
    }

    .chat-message {
      margin: 5px 0;
      padding: 5px;
      border-radius: 4px;
      background: #0f3460;
    }

    .forest-page {
      display: none;
      background: #16213e;
      padding: 20px;
      border-radius: 8px;
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      z-index: 100;
    }

    .forest-page.active {
      display: block;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>RPG Online Adventure</h1>
    <!-- Login Form -->
    <div id="loginForm" class="login-form">
      <h2>Login</h2>
      <input type="text" id="username" placeholder="Username">
      <input type="password" id="password" placeholder="Password">
      <button onclick="login()">Login</button>
      <button onclick="showRegister()">Register</button>
    </div>
    <!-- Register Form -->
    <div id="registerForm" class="login-form hidden">
      <h2>Register</h2>
      <input type="text" id="newUsername" placeholder="Username">
      <input type="password" id="newPassword" placeholder="Password">
      <select id="characterClass">
        <option value="warrior">Warrior</option>
        <option value="mage">Mage</option>
        <option value="archer">Archer</option>
      </select>
      <button onclick="register()">Create Character</button>
      <button onclick="returnToMenu()">Return to Menu</button>
    </div>
    <!-- Game UI -->
    <div id="gameUI" class="game-ui hidden">
      <div class="character">
        <div class="stats">
          <h2 id="playerName">Player</h2>
          <p>Class: <span id="playerClass">Warrior</span></p>
          <p>Level: <span id="playerLevel">1</span></p>
          <p>HP: <span id="playerHP">100</span>/<span id="playerMaxHP">100</span></p>
          <p>XP: <span id="playerXP">0</span>/<span id="playerNextLevel">100</span></p>
          <p>Stamina: <span id="playerStamina">100</span>/<span id="playerMaxStamina">100</span></p>
          <p>Gold: <span id="playerGold">0</span></p>
          <p>Wave: <span id="currentWave">1</span></p>
        </div>
      </div>
      <div class="actions">
        <button onclick="explore()">Explore</button>
        <button onclick="heal()">Heal (10 gold)</button>
        <button onclick="showInventoryPage()">Inventory</button>
        <button onclick="returnToMenu()">Return to Menu</button>
      </div>
      <div class="attacks" id="attackButtons">
      </div>
      <div class="battle-log" id="battleLog"></div>
      <div class="modes"></div>
    </div>
    <!-- Inventory Page -->
    <div id="inventoryPage" class="inventory-page">
      <button class="back-button" onclick="hideInventoryPage()">Back to Game</button>
      <div class="inventory-container">
        <div id="inventory" class="inventory">
          <!-- Inventory items will be listed here -->
        </div>
        <div id="equipped" class="equipped">
          <!-- Equipped items will be listed here -->
        </div>
      </div>
      <div class="crafting">
        <h3>Crafting</h3>
        <div id="craftingRecipes"></div>
      </div>
    </div>
    <!-- Explore Page -->
    <div id="explorePage" class="explore-page">
      <button class="back-button" onclick="hideExplorePage()">Back to Game</button>
      <h2>Choose Your Location</h2>
      <div class="location-grid">
        <div class="location-card" onclick="exploreLocation(&apos;forest&apos;)">
          <h3>Forest</h3>
          <p>A dense forest where wolves and other creatures lurk.</p>
          <p>Recommended Level: 1+</p>
        </div>
        <div class="location-card" onclick="exploreLocation(&apos;guild&apos;)">
          <h3>Adventurers Guild</h3>
          <p>A safe place where adventurers gather to chat and share stories.</p>
          <p>Recommended Level: 1+</p>
        </div>
      </div>
      <div id="guildChat" class="guild-chat hidden">
        <div id="chatMessages" class="chat-messages"></div>
        <div class="chat-input">
          <input type="text" id="chatInput" placeholder="Type your message...">
          <button onclick="sendChatMessage()">Send</button>
        </div>
      </div>
    </div>
    <!-- Forest Page -->
    <div id="forestPage" class="forest-page">
      <button class="back-button" onclick="hideForestPage()">Back to Locations</button>
      <h2>Forest</h2>
      <p>A dense forest where wolves and other creatures lurk.</p>
      <div class="actions">
        <button onclick="exploreForest()">Explore Forest</button>
        <button onclick="heal()">Heal (10 gold)</button>
        <button onclick="showInventoryPage()">Inventory</button>
      </div>
      <div class="character">
        <div class="stats">
          <h2 id="forestPlayerName">Player</h2>
          <p>Class: <span id="forestPlayerClass">Warrior</span></p>
          <p>Level: <span id="forestPlayerLevel">1</span></p>
          <p>HP: <span id="forestPlayerHP">100</span>/<span id="forestPlayerMaxHP">100</span></p>
          <p>XP: <span id="forestPlayerXP">0</span>/<span id="forestPlayerNextLevel">100</span></p>
          <p>Stamina: <span id="forestPlayerStamina">100</span>/<span id="forestPlayerMaxStamina">100</span></p>
          <p>Gold: <span id="forestPlayerGold">0</span></p>
          <p>Wave: <span id="forestCurrentWave">1</span></p>
        </div>
      </div>
      <div id="forestAttackButtons" class="attacks"></div>
      <div id="forestBattleLog" class="battle-log"></div>
      <div id="forestModes" class="modes"></div>
    </div>
    <!-- Admin Panel -->
    <div id="adminPanel" class="admin-panel hidden">
      <h2>Admin Panel</h2>
      <div>
        <h3>Create Enemy</h3>
        <input type="text" id="enemyName" placeholder="Enemy Name">
        <input type="number" id="enemyHP" placeholder="HP">
        <input type="number" id="enemyDamage" placeholder="Base Damage">
        <input type="number" id="enemyXP" placeholder="XP Reward">
        <input type="number" id="enemyLevel" placeholder="Level">
        <input type="number" id="enemyMinWave" placeholder="Min Wave">
        <input type="number" id="enemyMaxWave" placeholder="Max Wave (optional)">
        <select id="enemyElement">
          <option value>Select Element</option>
          <option value="WATER">Water</option>
          <option value="FIRE">Fire</option>
          <option value="GRASS">Grass</option>
          <option value="LIGHT">Light</option>
          <option value="DARK">Dark</option>
          <option value="SHADOW">Shadow</option>
          <option value="SPACE">Space</option>
          <option value="ICE">Ice</option>
          <option value="EARTH">Earth</option>
        </select>
        <button onclick="addEnemyAttack()">Add Attack</button>
        <div id="enemyAttacks">
          <!-- Attack elements will be added here -->
        </div>
        <button onclick="createEnemy()">Create Enemy</button>
        <button onclick="returnToMenu()">Return to Menu</button>
      </div>
      <div id="enemyList">
        <h3>Enemy List</h3>
        <div id="enemyItemTemplate">
          <div>
            &#x24;{enemy.name} (Level &#x24;{enemy.level}) - Element: &#x24;{enemy.element || &apos;none&apos;}<br>
            HP: &#x24;{enemy.hp}, Base DMG: &#x24;{enemy.damage}, XP: &#x24;{enemy.xp}<br>
            Spawn: &#x24;{enemy.spawnChance}% (Min Wave: &#x24;{enemy.minWave}&#x24;{enemy.maxWave ? `, Max Wave: &#x24;{enemy.maxWave}` : &apos;&apos;})
            &#x24;{enemy.mode ? `<br>Mode: &#x24;{enemy.mode.name} (&#x24;{enemy.mode.element || &apos;normal&apos;})` : &apos;&apos;}
            &#x24;{attacksHtml}
            <br><strong>Drops:</strong>&#x24;{dropsHtml}
          </div>
        </div>
        <!-- Example Enemy Item -->
        <div class="enemy">
          <span>Goblin</span>
          <button class="edit-enemy-btn" onclick="editEnemy(0)">Edit</button>
        </div>
        <!-- Add more enemies as needed -->
      </div>
      <div>
        <h3>Create Attack</h3>
        <input type="text" id="attackName" placeholder="Attack Name">
        <input type="number" id="attackDamage" placeholder="Attack Damage">
        <input type="number" id="attackStamina" placeholder="Stamina Cost">
        <input type="number" id="attackLevelReq" placeholder="Level Required">
        <select id="attackClassReq">
          <option value="any">Any Class</option>
          <option value="warrior">Warrior Only</option>
          <option value="mage">Mage Only</option>
          <option value="archer">Archer Only</option>
        </select>
        <select id="attackElement">
          <option value>Select Element</option>
          <option value="WATER">Water</option>
          <option value="FIRE">Fire</option>
          <option value="GRASS">Grass</option>
          <option value="LIGHT">Light</option>
          <option value="DARK">Dark</option>
          <option value="SHADOW">Shadow</option>
          <option value="SPACE">Space</option>
          <option value="ICE">Ice</option>
          <option value="EARTH">Earth</option>
        </select>
        <select id="attackWeaponReq">
          <option value="none">No Weapon Required</option>
          <option value="weapon">Requires Weapon</option>
        </select>
        <select id="attackItemReq1" class="attack-item-req">
          <option value="none">No Item Required</option>
        </select>
        <select id="attackItemReq2" class="attack-item-req">
          <option value="none">No Item Required</option>
        </select>
        <select id="attackItemReq3" class="attack-item-req">
          <option value="none">No Item Required</option>
        </select>
        <button onclick="createAttack()">Create Attack</button>
      </div>
      <div id="attackList">
        <h3>Attack List</h3>
        <!-- Attacks will be listed here -->
      </div>
      <!-- Add to admin panel -->
      <div>
        <h3>Create Mode</h3>
        <input type="text" id="modeName" placeholder="Mode Name">
        <input type="number" id="modeHPBonus" placeholder="HP Bonus">
        <input type="number" id="modeStaminaBonus" placeholder="Stamina Bonus">  
        <input type="number" id="modeDamageBonus" placeholder="Damage Bonus">
        <input type="number" id="modeLevelReq" placeholder="Level Required">
        <select id="modeClassReq">
          <option value="any">Any Class</option>
          <option value="warrior">Warrior Only</option>
          <option value="mage">Mage Only</option>
          <option value="archer">Archer Only</option>
        </select>
        <select id="modeElement">
          <option value>Select Element</option>
          <option value="WATER">Water</option>
          <option value="FIRE">Fire</option>
          <option value="GRASS">Grass</option>
          <option value="LIGHT">Light</option>
          <option value="DARK">Dark</option>
          <option value="SHADOW">Shadow</option>
          <option value="SPACE">Space</option>
          <option value="ICE">Ice</option>
          <option value="EARTH">Earth</option>
        </select>
        <select id="modeItemReq1" class="mode-item-req">
          <option value="none">No Item Required</option>
        </select>
        <select id="modeItemReq2" class="mode-item-req">
          <option value="none">No Item Required</option>
        </select>
        <select id="modeItemReq3" class="mode-item-req">
          <option value="none">No Item Required</option>
        </select>
        <button onclick="createMode()">Create Mode</button>
      </div>
      <div id="modeList">
        <h3>Mode List</h3>
        <!-- Modes will be listed here -->
      </div>
      <div>
        <h3>Create/Edit Item</h3>
        <input type="text" id="itemName" placeholder="Item Name">
        <select id="itemType">
          <option value="weapon">Weapon</option>
          <option value="armor">Armor</option>
          <option value="accessory">Accessory</option>
          <option value="material">Material</option>
        </select>
        <select id="itemClass">
          <option value="warrior">Warrior</option>
          <option value="mage">Mage</option> 
          <option value="archer">Archer</option>
          <option value="any">Any Class</option>
        </select>
        <input type="number" id="itemStat" placeholder="Damage/Defense/Bonus">
        <input type="number" id="itemDropChance" placeholder="Drop Chance (%)">
        <input type="number" id="itemMinLevel" placeholder="Minimum Level">
        <button onclick="createItem()">Create Item</button>
      </div>
      <div id="itemList">
        <h3>Item List</h3>
        <!-- Items will be listed here -->
      </div>
      <div>
        <h3>Create/Edit Crafting Recipe</h3>
        <input type="text" id="recipeName" placeholder="Recipe Name">
        <select id="recipeType">
          <option value="weapon">Weapon</option>
          <option value="armor">Armor</option>
          <option value="accessory">Accessory</option>
        </select>
        <input type="number" id="recipeStat" placeholder="Damage/Defense/Bonus">
        <input type="number" id="recipeMinLevel" placeholder="Minimum L
