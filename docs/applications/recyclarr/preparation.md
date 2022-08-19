Here is the exact configuration I used in the video

```
# A starter config to use with Recyclarr. Most values are set to "reasonable defaults". Update the
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
    api_key: 4b3bd4faeae244989783751d8afc0153

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

# Configuration specific to Radarr.
radarr:
  # Set the URL/API Key to your actual instance
  - base_url: http://radarr-custom-app.ix-radarr.svc.cluster.local:7878
    api_key: b4abe13930d64374af812cb55579a29a

    # Which quality definition in the guide to sync to Radarr. Only choice right now is 'movie'
    quality_definition:
      type: movie

    # Set to 'true' to automatically remove custom formats from Radarr when they are removed from
    # the guide or your configuration. This will NEVER delete custom formats you manually created!
    delete_old_custom_formats: true

    custom_formats:
      # A list of custom formats to sync to Radarr. Must match the "trash_id" in the guide JSON.
      - trash_ids:
          - 9170d55c319f4fe40da8711ba9d8050d # x265
          - e77382bcfeba57cb83744c9c5449b401 # 7.1 Surround
          - 89dac1be53d5268a7e10a19d3c896826 # 2.0 Stereo
          - 205125755c411c3b8622ca3175d27b37 # 3.0 Sound
          - 240770601cc226190c367ef59aba7463 # AAC
          - c20f169ef63c5f40c2def54abaf4438e # WEB Tier 01
          - 2f22d89048b01681dde8afe203bf2e95 # DTS X
          - b124be9b146540f8e62f98fe32e49a2a # 1.0 Mono
          - 90cedc1fea7ea5d11298bebd3d1d3223 # EVO (no WEBDL)
          - 4da96773192a51cf96178212642ca3bb # UHD (LEGi0N)
          - 8cd3ac70db7ac318cf9a0e01333940a4 # SiC
          - 5c44f52a8714fdd79bb4d98e2673be1f # Retags
          - 570bc9ebecd92723d2d21500f4be314c # Remaster
          - 58d6a88f13e2db7f5059c41047876f00 # DV
          - f2aacebe2c932337fe352fa6e42c1611 # 9.1 Surround
          - 403f3f6266b90439cacc1e07cae4dc2d # HQ-Remux
          - e9001909a4c88013a359d0b9920d7bea # Theatrical Cut
          - 185f1dd7264c4562b9022d963ac37424 # DD+
          - c20c8647f2746a1f4c4262b0fbbeeeae # HD Bluray Tier 02
          - b3b3a6ac74ecbd56bcdbefa4799fb9df # AMZN
          - e0c07d59beb37348e975a930d5e50319 # Criterion Collection
          - 4b900e171accbfb172729b63323ea8ca # Multi
          - 90a6f9a284dff5103f6346090e6280c8 # LQ
          - b8cd450cbfa689c0259a01d9e29ba3d6 # 3D
          - 0f12c086e289cf966fa5948eac571f44 # Hybrid
          - a061e2e700f81932daf888599f8a8273 # Opus
          - 957d0f44b592285f26449575e8b1167e # Special Edition
          - 0d91270a7255a1e388fa85e959f359d8 # FreeLeech
          - 2899d84dc9372de3408e6d8cc18e9666 # x264
          - dfb86d5941bc9075d6af23b09c2aeecd # HDR10
          - 2a6039655313bf5dab1e43523b62c374 # MA
          - a570d4a0e56a2874b64e5bfa55202a1b # FLAC
          - 496f355514737f7d83bf7aa4d24f8169 # TrueHD ATMOS
          - 77ff61788dfe1097194fd8743d7b4524 # 5.1 Surround
          - ffebc267e9c98d3d383f37b238550079 # UHD (W4NK3R)
          - ae9b7c9ebde1f3bd336a8cbd1ec4c5e5 # No-RlsGroup
          - 9de657fd3d327ecf144ec73dfe3a3e9a # Dutch Groups
          - 9364dd386c9b4a1100dde8264690add7 # HLG
          - 839bea857ed2c0a8e084f3cbdbd65ecb # x265 (no HDR/DV)
          - 1af239278386be2919e1bcee0bde047e # DD+ ATMOS
          - 26fa26253af4001701fedb56cec376dc # HQ-WEBDL
          - 08d6d8834ad9ec87b1dc7ec8148e7a1f # PQ
          - dcf3ec6938fa32445f590a4da84256cd # DTS-HD MA
          - e23edd2482476e595fb990b12e7c609c # DV HDR10
          - 3a3ff47579026e76d6504ebea39390de # Remux Tier 01
          - f9f847ac70a0af62ea4a08280b859636 # DTS-ES
          - ed38b889b31be83fda192888e2286d83 # BR-DISK
          - ed27ebfef2f323e964fb1f61391bcb35 # HD Bluray Tier 01
          - ff86c4326018682f817830ced463332b # MPEG2
          - 55d53828b9d81cbe20b02efd00aa0efd # DV HLG
          - 5763d1b0ce84aff3b21038eea8e9b8ad # HMAX
          - eca37840c13c6ef2dd0262b141a5482f # 4K Remaster
          - 1c7d7b04b15cc53ea61204bebbcc1ee2 # HQ
          - 9f6cbff8cfe4ebbc1bde14c7b7bec0de # IMAX Enhanced
          - fb392fb0d61a010ae38e49ceaa24a1ef # 2160p
          - afeb99e5db09290546f742503ce1cdb6 # UHD (DON)
          - 3472d276482257d68f7836a55ca24877 # APTV
          - e36a0ba1bc902b26ee40818a1d59b8bd # PMTP
          - 373b58bd188fc00c817bd8c7470ea285 # 4.0 Sound
          - 1d433e1e075704f1a8a1ae3e1c371460 # Flights (no IMAX)
          - 66aaa8c2c03c0191a95f0d655b75ab10 # UHD (CtrlHD)
          - 170b1d363bd8516fbf3a3eb05d4faff6 # NF
          - b6832f586342ef70d9c128d40c07b872 # Bad Dual Groups
          - c2998bd0d90ed5621d8df281e839436e # DD
          - 923b6abef9b17f937fab56cfcf89e1f1 # DV (WEBDL)
          - 403816d65392c79236dcb6dd591aeda4 # WEB Tier 02
          - 2a4d9069cc1fe3242ff9bdaebed239bb # HDR (undefined)
          - 4a3b087eea2ce012fcc1ce319259a3be # Anime Dual Audio
          - 84272245b2988854bfb76a16e60baea5 # DSNP
          - 5153ec7413d9dae44e24275589b5e944 # BHDStudio
          - 820b09bb9acbfde9c35c71e0e565dad8 # 1080p
          - e7c2fcae07cbada050a0af3357491d7b # PCM
          - 65be7ce5ec4c31e684c7b8368b8bd6bb # UHD (SPHD)
          - ff5bc9e8ce91d46c997ca3ac6994d6f8 # FraMeSToR
          - a3e19f8f627608af0211acd02bf89735 # DV SDR
          - 417804f7f2c4308c1f4c5d380d4c4475 # ATMOS (undefined)
          - af94e0fe497124d1f9ce732069ec8c3b # WEB Tier 03
          - 0a3f082873eb454bde444150b70253cc # Extras
          - 526d445d4c16214309f0fd2b3be18a89 # Hulu
          - b974a6cd08c1066250f1f177d7aa1225 # HDR10+
          - 9f98181fe5a3fbeb0cc29340da2a468a # Remux Tier 02
          - c9fd353f8f5f1baf56dc601c4cb29920 # PCOK
          - 8e109e50e0a0b83a5098b056e13bf6db # DTS-HD HRA
          - 7357cf5161efbf8c4d5d0c30b4815ee2 # Obfuscated
          - ae43b294509409a6a13919dedd4764c4 # Repack2
          - e61e28db95d22bedcadf030b8f156d96 # HDR
          - eecf3a857724171f968a66cb5719e152 # IMAX
          - 3cafb66171b47f226146a0770576870f # TrueHD
          - b2be17d608fc88818940cd1833b0b24c # 720p
          - 6fd7b090c3f7317502ab3b63cc7f51e3 # 6.1 Surround
          - 6ba9033150e7896bdc9ec4b44f2b230f # MP3
          - ac49fdbf6a662d380556f40ff4856f29 # UHD (WEBDV)
          - 1c1a4c5e823891c75bc50380a6866f73 # DTS
          - 96848626e1570c122aba8642fe2714a2 # UHD (HQMUX)
          - e7718d7a3ce595f289bfee26adc178f5 # Repack/Proper

        # Uncomment the below properties to specify one or more quality profiles that should be
        # updated with scores from the guide for each custom format. Without this, custom formats
        # are synced to Radarr but no scores are set in any quality profiles.
        quality_profiles:
          - name: HD
#           - name: Quality Profile 2
#            #score: -9999 # Optional score to assign to all CFs. Overrides scores in the guide.
#            #reset_unmatched_scores: true # Optionally set other scores to 0 if they are not listed in 'names' above.
```