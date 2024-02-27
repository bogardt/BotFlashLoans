# BotFlashLoans

![image](https://github.com/bogardt/BotFlashLoans/assets/16918134/c5ebe449-eb50-4872-b9fb-33ae40fcfde1)



sequenceDiagram
    participant ArbitrageBot as Arbitrage (C#)
    participant WebSocketAPI as WebSocket/API Service
    participant ArbitrageContract as Arbitrage Smart Contract
    participant DeFiPlatforms as DeFi Platforms (Uniswap and SushiSwap)
    
    ArbitrageBot->>WebSocketAPI: Requests market data
    WebSocketAPI-->>ArbitrageBot: Returns market data
    ArbitrageBot->>ArbitrageBot: Analyzes arbitrage opportunity
    ArbitrageBot->>ArbitrageContract: Initiates arbitrage with details
    ArbitrageContract->>DeFiPlatforms: Requests flash loan (optional)
    DeFiPlatforms-->>ArbitrageContract: Grants flash loan (optional)
    ArbitrageContract->>Uniswap: Executes swap if advantageous
    Uniswap-->>ArbitrageContract: Returns swapped tokens
    ArbitrageContract->>SushiSwap: Executes swap if advantageous
    SushiSwap-->>ArbitrageContract: Returns swapped tokens
    ArbitrageContract->>DeFiPlatforms: Repays flash loan with fees (optional)
    ArbitrageContract-->>ArbitrageBot: Transfers profits
