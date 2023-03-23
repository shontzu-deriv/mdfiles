# DIEL

#### table below is an comparison of the different financial regulator and what DIEL is all about

|             \              |        `financial_company`         |                    `gaming_company`                     |
| :------------------------: | :--------------------------------: | :-----------------------------------------------------: |
|        **country**         |               Malta                |            Saint Vincent and the Grenadines             |
|   **allowed countires**    |                EUR                 |                           ROW                           |
|       **regulator**        | Malta Financial Services Authority |                  Financial Commission                   |
|  **counterparty company**  | Deriv Investments (Europe) Limited |                     Deriv (SVG) LLC                     |
|       **shortcode**        |            maltainvest             |                           svg                           |
|      **account type**      |                 MF                 |                           CR                            |
|        **markets**         | cryptocurrency, forex, synthetics  | commodities, cryptocurrency, forex, indices, syntehtics |
|        **currency**        |            EUR GBP USD             |       AUD BTC ETH EUR GBP LTC USD USDC UST eUSDT        |
|    **default currency**    |                EUR                 |                           USD                           |
|        **leverage**        |                 30                 |                        100-1000                         |
| **-ve balance protection** |             all assets             |                     synthetics only                     |
|                            |                                    |                                                         |
|       **multiplier**       |                 /                  |                            /                            |
|         **option**         |                 X                  |                            /                            |
|        **platform**        |              DTrader               |       DTrader, DBot, SmartTrader, and Binary Bot        |
|                            |                                    |                                                         |
|          **CFD**           |                 /                  |                            /                            |
|        **platform**        |                DMT5                |                      DMT5, Deriv X                      |

\*options: asian, callput, callputequal, callputspread, digits, endsinout, highlowticks, lookback, reset, runs, staysinout, touchnotouch

# Traders-hub-store.js

#### the purpose of this documentation is to help myself understand the roles of all the variables present in here and how they are needed in the application

### `is_pre_appstore`

true when user is in tradershub, false when not in tradershub

### `account_type_card: observable`

```JavaScript
// account-type-modal.tsx line 12
const derived_account: TAccountType = {
    title_and_type: localize('Derived'),
    icon: 'Derived',
    description: localize('Trade CFDs on MT5 with Derived indices that simulate real-world market movements.'),
};

const financial_account: TAccountType = {
    title_and_type: localize('Financial'),
    icon: 'Financial',
    description: localize('Trade CFDs on MT5 with forex, stock indices, commodities, and cryptocurrencies.'),
};
```

```JavaScript
// account-type-modal.tsx line 105
account_type_card === 'Derived'
            ? setAccountType({ category: 'real', type: 'synthetic' })
            : setAccountType({ category: 'real', type: 'financial' });
```

### `available_cfd_accounts: observable`

```JavaScript
available_cfd_accounts = all_available_accounts.map(account => {
    return {
        ...account,
        description: account.description,
    };
}

const all_available_accounts = [...getCFDAvailableAccount()];
```

where `all_available_accounts` makes a function call to `getCFDAvailableAccount()` that returns an array of objects

```JavaScript
export const getCFDAvailableAccount = () => [
    {
        name: 'Derived',
        description: localize('Trade CFDs on MT5 with synthetics, baskets, and derived FX.'),
        platform: CFD_PLATFORMS.MT5,
        market_type: 'synthetic',
        icon: 'Derived',
        availability: 'Non-EU',
    },
    {
        name: 'Deriv X',
        description: localize('Trade CFDs on Deriv X with financial markets and our Derived indices.'),
        platform: CFD_PLATFORMS.DXTRADE,
        market_type: 'all',
        icon: 'DerivX',
        availability: 'Non-EU',
    },
    {
        name: 'Deriv cTrader',
        description: localize(
            'Trade CFDs on forex, commodities, cryptocurrencies, stocks, stock indices, and derived indices.'
        ),
        platform: CFD_PLATFORMS.CTRADER,
        market_type: 'all',
        icon: 'CTrader',
        availability: 'Non-EU',
    },
];
```

### `available_dxtrade_accounts`, `available_ctrader_accounts`, `available_mt5_accounts` `:observable`

a filter method to filter `available_cfd_accounts[]` based on **platform** (dTrader, cTrader, derivX, derivEZ) and assign to `available_dxtrade_accounts[]`

```JavaScript
available_dxtrade_accounts = available_cfd_accounts.filter(
    account => account.platform === CFD_PLATFORMS.DXTRADE
);
```

### `available_platforms: observable`

makes a funciton call to JSON `platform_appstore{}` then filter it based on **location** (EU, ROW) and assign to `available_platforms[]`

```JSON
"platforms_appstore": {
        "trader": {
            "name": "DTrader",
            "icon": "DTrader",
            "availability": "All"
        },
        "dbot": {
            "name": "DBot",
            "icon": "DBot",
            "availability": "Non-EU"
        },
        "smarttrader": {
            "name": "SmartTrader",
            "icon": "SmartTrader",
            "availability": "Non-EU"
        },
        "bbot": {
            "name": "Binary Bot",
            "icon": "BinaryBot",
            "availability": "Non-EU"
        },
        "go": {
            "name": "Deriv GO",
            "icon": "DerivGo",
            "availability": "Non-EU"
        }
    }
```

### `cfd_demo_balance: observable`

### `cfd_real_balance: observable`

### `combined_cfd_mt5_accounts: observable`

### `is_account_transfer_modal_open: observable`

### `is_account_type_modal_visible: observable`

### `is_regulators_compare_modal_visible: observable`

### `is_failed_verification_modal_visible: observable`

### `is_balance_calculating: observable`

### `is_tour_open: observable`

### `modal_data: observable`

### `is_onboarding_visited: observable`

### `platform_demo_balance: observable`

### `platform_real_balance: observable`

### `selected_account: observable`

### `selected_account_type: observable`

### `selected_platform_type: observable`

### `selected_region: observable`

### `open_failed_verification_for: observable`

### `can_get_more_cfd_mt5_accounts: computed`

### `closeModal: action.bound`

### `content_flag: computed`

### `getAccount: action.bound`

### `getAvailableCFDAccounts: action.bound`

### `getAvailableDxtradeAccounts: action.bound`

### `getAvailableCTraderAccounts: action.bound`

### `getExistingAccounts: action.bound`

### `handleTabItemClick: action.bound`

### `has_any_real_account: computed`

### `is_demo_low_risk: computed`

### `is_demo: computed`

### `is_eu_selected: computed`

### `is_real: computed`

### `is_currency_switcher_disabled_for_mf: computed`

### `no_CR_account: computed`

### `no_MF_account: computed`

### `multipliers_account_status: computed`

### `openDemoCFDAccount: action.bound`

### `openModal: action.bound`

### `openRealAccount: action.bound`

### `selectAccountType: action.bound`

### `selectAccountTypeCard: action.bound`

### `switchToCRAccount: action.bound`

### `selectRegion: action.bound`

### `setCombinedCFDMT5Accounts: action.bound`

### `setSelectedAccount: action.bound`

### `setTogglePlatformType: action.bound`

### `should_show_exit_traders_modal: computed`

### `show_eu_related_content: computed`

### `startTrade: action.bound`

### `toggleAccountTransferModal: action.bound`

### `toggleAccountTypeModalVisibility: action.bound`

### `setIsOnboardingVisited: action.bound`

### `toggleFailedVerificationModalVisibility: action.bound`

### `openFailedVerificationModal: action.bound`

### `toggleIsTourOpen: action.bound`

### `toggleRegulatorsCompareModal: action.bound`

### `updatePlatformBalance: action.bound`

### `showTopUpModal: action.bound`
