Here is the exact configuration I used in the video

```
# Starter config to use with Recyclarr. Most values are set to "reasonable defaults". Update the
# values below as needed for your instance. You will be required to update the API Key and URL for
# each instance you want to use.
#
# Many optional settings have been omitted to keep this template simple.
#
# For more details on the configuration, see the Configuration Reference on the wiki here:
# https://github.com/recyclarr/recyclarr/wiki/Configuration-Reference

# Configuration specific to Sonarr
sonarr:
  # Set the URL/API Key to your actual instance
  - base_url: http://sonarr-custom-app.ix-sonarr.svc.cluster.local:8989
    api_key: sdfgsadfhadfhadfgsdfgs

    # Quality definitions from the guide to sync to Sonarr. Choice: anime, series, hybrid
    quality_definition: hybrid

    # Release profiles from the guide to sync to Sonarr.
    # You can optionally add tags and make negative scores strictly ignored
    release_profiles:
      # Series
      - trash_ids:
          - EBC725268D687D588A20CBC5F97E538B # Low Quality Groups
          - 1B018E0C53EC825085DD911102E2CA36 # Release Sources (Streaming Service)
          - 71899E6C303A07AF0E4746EFF9873532 # P2P Groups + Repack/Proper
        tags: [non-anime]
      # Anime (Uncomment below if you want it)
      - trash_ids:
          - d428eda85af1df8904b4bbe4fc2f537c # Anime - First release profile
          - 6cd9e10bb5bb4c63d2d7cd3279924c7b # Anime - Second release profile
        tags: [anime]
      # Optionals
      - trash_ids: [76e060895c5b8a765c310933da0a5357] # Optionals
        filter:
          exclude:
            - cec8880b847dd5d31d29167ee0112b57 # Golden rule
        tags: [non-anime]


# Configuration specific to Radarr.
radarr:
  # Set the URL/API Key to your actual instance
  - base_url: http://radarr-custom-app.ix-radarr.svc.cluster.local:7878
    api_key: asdfasdfasdfasdfsgsdfhsdffghsdffg

    # Which quality definition in the guide to sync to Radarr. Only choice right now is 'movie'
    quality_definition:
      type: movie

    # Set to 'true' to automatically remove custom formats from Radarr when they are removed from
    # the guide or your configuration. This will NEVER delete custom formats you manually created!
    delete_old_custom_formats: true

    custom_formats:
      # A list of custom formats to sync to Radarr. Must match the "trash_id" in the guide JSON.
      - trash_ids:
          - 240770601cc226190c367ef59aba7463 # AAC
          - 373b58bd188fc00c817bd8c7470ea285 # 4.0 Sound
          - 496f355514737f7d83bf7aa4d24f8169 # TrueHD ATMOS
          - a061e2e700f81932daf888599f8a8273 # Opus
          - ed38b889b31be83fda192888e2286d83 # BR-DISK
          - 0f12c086e289cf966fa5948eac571f44 # Hybrid
          - 9de657fd3d327ecf144ec73dfe3a3e9a # Dutch Groups
          - 957d0f44b592285f26449575e8b1167e # Special Edition
          - b974a6cd08c1066250f1f177d7aa1225 # HDR10+
          - e0c07d59beb37348e975a930d5e50319 # Criterion Collection
          - b3b3a6ac74ecbd56bcdbefa4799fb9df # AMZN
          - 3a3ff47579026e76d6504ebea39390de # Remux Tier 01
          - 923b6abef9b17f937fab56cfcf89e1f1 # DV (WEBDL)
          - 403816d65392c79236dcb6dd591aeda4 # WEB Tier 02
          - 820b09bb9acbfde9c35c71e0e565dad8 # 1080p
          - afeb99e5db09290546f742503ce1cdb6 # UHD (DON)
          - ac49fdbf6a662d380556f40ff4856f29 # UHD (WEBDV)
          - eca37840c13c6ef2dd0262b141a5482f # 4K Remaster
          - ffebc267e9c98d3d383f37b238550079 # UHD (W4NK3R)
          - 8cd3ac70db7ac318cf9a0e01333940a4 # SiC
          - ff5bc9e8ce91d46c997ca3ac6994d6f8 # FraMeSToR
          - 96848626e1570c122aba8642fe2714a2 # UHD (HQMUX)
          - 9170d55c319f4fe40da8711ba9d8050d # x265
          - ff86c4326018682f817830ced463332b # MPEG2
          - 6fd7b090c3f7317502ab3b63cc7f51e3 # 6.1 Surround
          - 2899d84dc9372de3408e6d8cc18e9666 # x264
          - 4da96773192a51cf96178212642ca3bb # UHD (LEGi0N)
          - 5c44f52a8714fdd79bb4d98e2673be1f # Retags
          - c20c8647f2746a1f4c4262b0fbbeeeae # HD Bluray Tier 02
          - 170b1d363bd8516fbf3a3eb05d4faff6 # NF
          - c2998bd0d90ed5621d8df281e839436e # DD
          - a570d4a0e56a2874b64e5bfa55202a1b # FLAC
          - ae43b294509409a6a13919dedd4764c4 # Repack2
          - 65be7ce5ec4c31e684c7b8368b8bd6bb # UHD (SPHD)
          - e9001909a4c88013a359d0b9920d7bea # Theatrical Cut
          - 08d6d8834ad9ec87b1dc7ec8148e7a1f # PQ
          - 90cedc1fea7ea5d11298bebd3d1d3223 # EVO (no WEBDL)
          - fb392fb0d61a010ae38e49ceaa24a1ef # 2160p
          - dcf3ec6938fa32445f590a4da84256cd # DTS-HD MA
          - 185f1dd7264c4562b9022d963ac37424 # DD+
          - 9364dd386c9b4a1100dde8264690add7 # HLG
          - af94e0fe497124d1f9ce732069ec8c3b # WEB Tier 03
          - f2aacebe2c932337fe352fa6e42c1611 # 9.1 Surround
          - e36a0ba1bc902b26ee40818a1d59b8bd # PMTP
          - b124be9b146540f8e62f98fe32e49a2a # 1.0 Mono
          - 570bc9ebecd92723d2d21500f4be314c # Remaster
          - a3e19f8f627608af0211acd02bf89735 # DV SDR
          - 2a6039655313bf5dab1e43523b62c374 # MA
          - e7718d7a3ce595f289bfee26adc178f5 # Repack/Proper
          - 84272245b2988854bfb76a16e60baea5 # DSNP
          - 5763d1b0ce84aff3b21038eea8e9b8ad # HMAX
          - 4b900e171accbfb172729b63323ea8ca # Multi
          - dfb86d5941bc9075d6af23b09c2aeecd # HDR10
          - 0a3f082873eb454bde444150b70253cc # Extras
          - 3472d276482257d68f7836a55ca24877 # APTV
          - 7357cf5161efbf8c4d5d0c30b4815ee2 # Obfuscated
          - e77382bcfeba57cb83744c9c5449b401 # 7.1 Surround
          - 9f98181fe5a3fbeb0cc29340da2a468a # Remux Tier 02
          - 8e109e50e0a0b83a5098b056e13bf6db # DTS-HD HRA
          - 1d433e1e075704f1a8a1ae3e1c371460 # Flights (no IMAX)
          - 205125755c411c3b8622ca3175d27b37 # 3.0 Sound
          - b6832f586342ef70d9c128d40c07b872 # Bad Dual Groups
          - 3cafb66171b47f226146a0770576870f # TrueHD
          - c20f169ef63c5f40c2def54abaf4438e # WEB Tier 01
          - ae9b7c9ebde1f3bd336a8cbd1ec4c5e5 # No-RlsGroup
          - 58d6a88f13e2db7f5059c41047876f00 # DV
          - b2be17d608fc88818940cd1833b0b24c # 720p
          - f9f847ac70a0af62ea4a08280b859636 # DTS-ES
          - 2a4d9069cc1fe3242ff9bdaebed239bb # HDR (undefined)
          - 417804f7f2c4308c1f4c5d380d4c4475 # ATMOS (undefined)
          - e7c2fcae07cbada050a0af3357491d7b # PCM
          - 526d445d4c16214309f0fd2b3be18a89 # Hulu
          - e23edd2482476e595fb990b12e7c609c # DV HDR10
          - c9fd353f8f5f1baf56dc601c4cb29920 # PCOK
          - 2f22d89048b01681dde8afe203bf2e95 # DTS X
          - e61e28db95d22bedcadf030b8f156d96 # HDR
          - 6ba9033150e7896bdc9ec4b44f2b230f # MP3
          - 1af239278386be2919e1bcee0bde047e # DD+ ATMOS
          - 55d53828b9d81cbe20b02efd00aa0efd # DV HLG
          - 89dac1be53d5268a7e10a19d3c896826 # 2.0 Stereo
          - 9f6cbff8cfe4ebbc1bde14c7b7bec0de # IMAX Enhanced
          - eecf3a857724171f968a66cb5719e152 # IMAX
          - 839bea857ed2c0a8e084f3cbdbd65ecb # x265 (no HDR/DV)
          - 66aaa8c2c03c0191a95f0d655b75ab10 # UHD (CtrlHD)
          - b8cd450cbfa689c0259a01d9e29ba3d6 # 3D
          - 77ff61788dfe1097194fd8743d7b4524 # 5.1 Surround
          - 1c1a4c5e823891c75bc50380a6866f73 # DTS
          - ed27ebfef2f323e964fb1f61391bcb35 # HD Bluray Tier 01
          - 90a6f9a284dff5103f6346090e6280c8 # LQ
        quality_profiles:
          - name: HD

      - trash_ids:
#          - b23eae459cc960816f2d6ba84af45055 # Dubs Only
          - 4a3b087eea2ce012fcc1ce319259a3be # Anime Dual Audio
          - b0fdc5897f68c9a68c70c25169f77447 # Anime LQ Groups
          - a5d148168c4506b55cf53984107c396e # 10bit
          - 06b6542a47037d1e33b15aa3677c2365 # Anime Raws
          - fb3ccc5d5cc8f77c9055d4cb4561dded # Anime BD Tier 01 (Top SeaDex Muxers)
          - 66926c8fa9312bc74ab71bf69aae4f4a # Anime BD Tier 02 (SeaDex Muxers)
          - fa857662bad28d5ff21a6e611869a0ff # Anime BD Tier 03 (SeaDex Muxers)
          - f262f1299d99b1a2263375e8fa2ddbb3 # Anime BD Tier 04 (SeaDex Muxers)
          - ca864ed93c7b431150cc6748dc34875d # Anime BD Tier 05 (Remuxes)
          - 9dce189b960fddf47891b7484ee886ca # Anime BD Tier 06 (FanSubs)
          - 1ef101b3a82646b40e0cab7fc92cd896 # Anime BD Tier 07 (P2P/Scene)
          - 6115ccd6640b978234cc47f2c1f2cadc # Anime BD Tier 08 (Mini Encodes)
          - 8167cffba4febfb9a6988ef24f274e7e # Anime Web Tier 01 (Muxers)
          - 8526c54e36b4962d340fce52ef030e76 # Anime Web Tier 02 (Top FanSubs)
          - 5b1a5d3df27396373b4ce236fc337eaa # Anime Web Tier 03 (SubsPlease)
          - 9edaeee9ea3bcd585da9b7c0ac3fc54f # Anime Web Tier 04 (Official Subs)
          - 22d953bbe897857b517928f3652b8dd3 # Anime Web Tier 05 (FanSubs)
          - a786fbc0eae05afe3bb51aee3c83a9d4 # Anime Web Tier 06 (FanSubs)
          - c259005cbaeb5ab44c06eddb4751e70c # v0
          - 5f400539421b8fcf71d51e6384434573 # v1
          - 3df5e6dfef4b09bb6002f732bed5b774 # v2
          - db92c27ba606996b146b57fbe6d09186 # v3
          - d4e5e842fad129a3c097bdb2d20d31a0 # v4
          - 60f6d50cbd3cfc3e9a8c00e3a30c3114 # VRV
        quality_profiles:
          - name: Anime
```
