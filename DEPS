# Note: The buildbots evaluate this file with CWD set to the parent
# directory and assume that the root of the checkout is in ./v8/, so
# all paths in here must match this assumption.

use_relative_paths = True

gclient_gn_args_file = 'build/config/gclient_args.gni'
gclient_gn_args = [
  # TODO(https://crbug.com/1137662, https://crbug.com/1080854)
  # Remove when migration is complete.
  'checkout_fuchsia_for_arm64_host',
  'checkout_google_benchmark',
]

vars = {
  # Fetches only the SDK boot images which match at least one of the whitelist
  # entries in a comma-separated list.
  #
  # Only the X64 and ARM64 QEMU images are downloaded by default. Developers
  # that need to boot on other target architectures or devices can opt to
  # download more boot images. Example of images include:
  #
  # Emulation:
  #   qemu.x64, qemu.arm64
  # Hardware:
  #   generic.x64, generic.arm64
  #
  # Wildcards are supported (e.g. "qemu.*").
  'checkout_fuchsia_boot_images': "qemu.x64,qemu.arm64",

  # TODO(https://crbug.com/1137662, https://crbug.com/1080854)
  # Remove when migration is complete.
  # By default, do not check out files required to run fuchsia tests in
  # qemu on linux-arm64 machines.
  'checkout_fuchsia_for_arm64_host': False,

  'checkout_instrumented_libraries': False,
  'checkout_ittapi': False,
  # Fetch clang-tidy into the same bin/ directory as our clang binary.
  'checkout_clang_tidy': False,
  'chromium_url': 'https://chromium.googlesource.com',
  'android_url': 'https://android.googlesource.com',
  'download_gcmole': False,
  'download_jsfunfuzz': False,
  'check_v8_header_includes': False,

  'checkout_google_benchmark' : False,

  # GN CIPD package version.
  'gn_version': 'git_revision:0d67e272bdb8145f87d238bc0b2cb8bf80ccec90',

  # luci-go CIPD package version.
  'luci_go': 'git_revision:67aba6e3373bb0b9e3ef9871362045736cd29b6e',

  # Three lines of non-changing comments so that
  # the commit queue can handle CLs rolling android_sdk_build-tools_version
  # and whatever else without interference from each other.
  'android_sdk_build-tools_version': '8LZujEmLjSh0g3JciDA3cslSptxKs9HOa_iUPXkOeYQC',
  # Three lines of non-changing comments so that
  # the commit queue can handle CLs rolling android_sdk_emulator_version
  # and whatever else without interference from each other.
  'android_sdk_emulator_version': 'A4EvXZUIuQho0QRDJopMUpgyp6NA3aiDQjGKPUKbowMC',
  # Three lines of non-changing comments so that
  # the commit queue can handle CLs rolling android_sdk_extras_version
  # and whatever else without interference from each other.
  'android_sdk_extras_version': 'ppQ4TnqDvBHQ3lXx5KPq97egzF5X2FFyOrVHkGmiTMQC',
  # Three lines of non-changing comments so that
  # the commit queue can handle CLs rolling android_sdk_patcher_version
  # and whatever else without interference from each other.
  'android_sdk_patcher_version': 'I6FNMhrXlpB-E1lOhMlvld7xt9lBVNOO83KIluXDyA0C',
  # Three lines of non-changing comments so that
  # the commit queue can handle CLs rolling android_sdk_platform-tools_version
  # and whatever else without interference from each other.
  'android_sdk_platform-tools_version': '8tF0AOj7Dwlv4j7_nfkhxWB0jzrvWWYjEIpirt8FIWYC',
  # Three lines of non-changing comments so that
  # the commit queue can handle CLs rolling android_sdk_platforms_version
  # and whatever else without interference from each other.
  'android_sdk_platforms_version': 'YMUu9EHNZ__2Xcxl-KsaSf-dI5TMt_P62IseUVsxktMC',
  # Three lines of non-changing comments so that
  # the commit queue can handle CLs rolling android_sdk_sources_version
  # and whatever else without interference from each other.
  'android_sdk_sources_version': '4gxhM8E62bvZpQs7Q3d0DinQaW0RLCIefhXrQBFkNy8C',
  # Three lines of non-changing comments so that
  # the commit queue can handle CLs rolling android_sdk_tools-lint_version
  # and whatever else without interference from each other.
  'android_sdk_cmdline-tools_version': 'V__2Ycej-H2-6AcXX5A3gi7sIk74SuN44PBm2uC_N1sC',
}

deps = {
  'build':
    Var('chromium_url') + '/chromium/src/build.git' + '@' + 'b3c270e43c03ad0b1cde3f34a88ba183fc073b10',
  'third_party/depot_tools':
    Var('chromium_url') + '/chromium/tools/depot_tools.git' + '@' + '364205c70ed16c00802b1c264e88d8e03a0b37ae',
  'third_party/icu':
    Var('chromium_url') + '/chromium/deps/icu.git' + '@' + '899e18383fd732b47e6978db2b960a1b2a80179b',
  'third_party/instrumented_libraries':
    Var('chromium_url') + '/chromium/src/third_party/instrumented_libraries.git' + '@' + '4d3867052d35b2171f2edbb3466fa8f7e2d11319',
  'buildtools':
    Var('chromium_url') + '/chromium/src/buildtools.git' + '@' + '2277272f7a7978c48f1b2c50d41af83485552235',
  'buildtools/clang_format/script':
    Var('chromium_url') + '/chromium/llvm-project/cfe/tools/clang-format.git' + '@' + '96636aa0e9f047f17447f2d45a094d0b59ed7917',
  'buildtools/linux64': {
    'packages': [
      {
        'package': 'gn/gn/linux-amd64',
        'version': Var('gn_version'),
      }
    ],
    'dep_type': 'cipd',
    'condition': 'host_os == "linux"',
  },
  'buildtools/mac': {
    'packages': [
      {
        'package': 'gn/gn/mac-amd64',
        'version': Var('gn_version'),
      }
    ],
    'dep_type': 'cipd',
    'condition': 'host_os == "mac"',
  },
  'buildtools/third_party/libc++/trunk':
    Var('chromium_url') + '/external/github.com/llvm/llvm-project/libcxx.git' + '@' + 'd9040c75cfea5928c804ab7c235fed06a63f743a',
  'buildtools/third_party/libc++abi/trunk':
    Var('chromium_url') + '/external/github.com/llvm/llvm-project/libcxxabi.git' + '@' + '196ba1aaa8ac285d94f4ea8d9836390a45360533',
  'buildtools/third_party/libunwind/trunk':
    Var('chromium_url') + '/external/github.com/llvm/llvm-project/libunwind.git' + '@' + 'd999d54f4bca789543a2eb6c995af2d9b5a1f3ed',
  'buildtools/win': {
    'packages': [
      {
        'package': 'gn/gn/windows-amd64',
        'version': Var('gn_version'),
      }
    ],
    'dep_type': 'cipd',
    'condition': 'host_os == "win"',
  },
  'base/trace_event/common':
    Var('chromium_url') + '/chromium/src/base/trace_event/common.git' + '@' + 'eb94f1c7aa96207f469008f29989a43feb2718f8',
  'third_party/android_ndk': {
    'url': Var('chromium_url') + '/android_ndk.git' + '@' + '27c0a8d090c666a50e40fceb4ee5b40b1a2d3f87',
    'condition': 'checkout_android',
  },
  'third_party/android_platform': {
    'url': Var('chromium_url') + '/chromium/src/third_party/android_platform.git' + '@' + 'ef64306e7772dea22df5f98102e6288da3510843',
    'condition': 'checkout_android',
  },
  'third_party/android_sdk/public': {
      'packages': [
          {
              'package': 'chromium/third_party/android_sdk/public/build-tools/30.0.1',
              'version': Var('android_sdk_build-tools_version'),
          },
          {
              'package': 'chromium/third_party/android_sdk/public/emulator',
              'version': Var('android_sdk_emulator_version'),
          },
          {
              'package': 'chromium/third_party/android_sdk/public/extras',
              'version': Var('android_sdk_extras_version'),
          },
          {
              'package': 'chromium/third_party/android_sdk/public/patcher',
              'version': Var('android_sdk_patcher_version'),
          },
          {
              'package': 'chromium/third_party/android_sdk/public/platform-tools',
              'version': Var('android_sdk_platform-tools_version'),
          },
          {
              'package': 'chromium/third_party/android_sdk/public/platforms/android-30',
              'version': Var('android_sdk_platforms_version'),
          },
          {
              'package': 'chromium/third_party/android_sdk/public/sources/android-29',
              'version': Var('android_sdk_sources_version'),
          },
          {
              'package': 'chromium/third_party/android_sdk/public/cmdline-tools',
              'version': Var('android_sdk_cmdline-tools_version'),
          },
      ],
      'condition': 'checkout_android',
      'dep_type': 'cipd',
  },
  'third_party/catapult': {
    'url': Var('chromium_url') + '/catapult.git' + '@' + '3f5c581d3b045f00847989a9611912e022021343',
    'condition': 'checkout_android',
  },
  'third_party/colorama/src': {
    'url': Var('chromium_url') + '/external/colorama.git' + '@' + '799604a1041e9b3bc5d2789ecbd7e8db2e18e6b8',
    'condition': 'checkout_android',
  },
  'third_party/fuchsia-sdk': {
    'url': Var('chromium_url') + '/chromium/src/third_party/fuchsia-sdk.git' + '@' + 'efa46583d89ea8c97523281d9f52a0d96472114d',
    'condition': 'checkout_fuchsia',
  },
  'third_party/googletest/src':
    Var('chromium_url') + '/external/github.com/google/googletest.git' + '@' + '4fe018038f87675c083d0cfb6a6b57c274fb1753',
  'third_party/google_benchmark/src': {
    'url': Var('chromium_url') + '/external/github.com/google/benchmark.git' + '@' + '7f27afe83b82f3a98baf58ef595814b9d42a5b2b',
    'condition': 'checkout_google_benchmark',
  },
  'third_party/jinja2':
    Var('chromium_url') + '/chromium/src/third_party/jinja2.git' + '@' + '11b6b3e5971d760bd2d310f77643f55a818a6d25',
  'third_party/markupsafe':
    Var('chromium_url') + '/chromium/src/third_party/markupsafe.git' + '@' + '0944e71f4b2cb9a871bcbe353f95e889b64a611a',
  'tools/swarming_client':
    Var('chromium_url') + '/infra/luci/client-py.git' + '@' + '1a072711d4388c62e02480fabc26c68c24494be9',
  'test/benchmarks/data':
    Var('chromium_url') + '/v8/deps/third_party/benchmarks.git' + '@' + '05d7188267b4560491ff9155c5ee13e207ecd65f',
  'test/mozilla/data':
    Var('chromium_url') + '/v8/deps/third_party/mozilla-tests.git' + '@' + 'f6c578a10ea707b1a8ab0b88943fe5115ce2b9be',
  'test/test262/data':
    Var('chromium_url') + '/external/github.com/tc39/test262.git' + '@' + '51666c5315ee674d3157544497d933310e2cd6b8',
  'test/test262/harness':
    Var('chromium_url') + '/external/github.com/test262-utils/test262-harness-py.git' + '@' + '4555345a943d0c99a9461182705543fb171dda4b',
  'third_party/qemu-linux-x64': {
      'packages': [
          {
              'package': 'fuchsia/qemu/linux-amd64',
              'version': '9cc486c5b18a0be515c39a280ca9a309c54cf994'
          },
      ],
      'condition': 'host_os == "linux" and checkout_fuchsia',
      'dep_type': 'cipd',
  },
  'third_party/qemu-mac-x64': {
      'packages': [
          {
              'package': 'fuchsia/qemu/mac-amd64',
              'version': '2d3358ae9a569b2d4a474f498b32b202a152134f'
          },
      ],
      'condition': 'host_os == "mac" and checkout_fuchsia',
      'dep_type': 'cipd',
  },
  'third_party/aemu-linux-x64': {
      'packages': [
          {
              'package': 'fuchsia/third_party/aemu/linux-amd64',
              'version': 'eNKL3iFnDydKoCyqA9rVhylE7ud5a_9wRt0b0HFtLvIC'
          },
      ],
      'condition': 'host_os == "linux" and checkout_fuchsia',
      'dep_type': 'cipd',
  },
  'third_party/aemu-mac-x64': {
      'packages': [
          {
              'package': 'fuchsia/third_party/aemu/mac-amd64',
              'version': 'T9bWxf8aUC5TwCFgPxpuW29Mfy-7Z9xCfXB9QO8MfU0C'
          },
      ],
      'condition': 'host_os == "mac" and checkout_fuchsia',
      'dep_type': 'cipd',
  },
  'tools/clang':
    Var('chromium_url') + '/chromium/src/tools/clang.git' + '@' + '1283870fa32612951b487e0a4b17145ff62ed1e6',
  'tools/luci-go': {
      'packages': [
        {
          'package': 'infra/tools/luci/isolate/${{platform}}',
          'version': Var('luci_go'),
        },
        {
          'package': 'infra/tools/luci/isolated/${{platform}}',
          'version': Var('luci_go'),
        },
        {
          'package': 'infra/tools/luci/swarming/${{platform}}',
          'version': Var('luci_go'),
        },
      ],
      'condition': 'host_cpu != "s390" and host_os != "aix"',
      'dep_type': 'cipd',
  },
  'tools/clang/dsymutil': {
    'packages': [
      {
        'package': 'chromium/llvm-build-tools/dsymutil',
        'version': 'M56jPzDv1620Rnm__jTMYS62Zi8rxHVq7yw0qeBFEgkC',
      }
    ],
    'condition': 'checkout_mac',
    'dep_type': 'cipd',
  },
  'third_party/perfetto':
    Var('android_url') + '/platform/external/perfetto.git' + '@' + '7cdc44f903d3bcfd1d0f67188bfa797a24756868',
  'third_party/protobuf':
    Var('chromium_url') + '/external/github.com/google/protobuf'+ '@' + 'b68a347f56137b4b1a746e8c7438495a6ac1bd91',
  'third_party/zlib':
    Var('chromium_url') + '/chromium/src/third_party/zlib.git'+ '@' + '2c183c9f93a328bfb3121284da13cf89a0f7e64a',
  'third_party/jsoncpp/source':
    Var('chromium_url') + '/external/github.com/open-source-parsers/jsoncpp.git'+ '@' + '9059f5cad030ba11d37818847443a53918c327b1',
  'third_party/ittapi': {
    # Force checkout ittapi libraries to pass v8 header includes check on
    # bots that has check_v8_header_includes enabled.
    'url': Var('chromium_url') + '/external/github.com/intel/ittapi' + '@' + 'b4ae0122ba749163096058b4f1bb065bf4a7de94',
    'condition': "checkout_ittapi or check_v8_header_includes",
  },
  'third_party/requests': {
      'url': Var('chromium_url') + '/external/github.com/kennethreitz/requests.git' + '@' + 'bfb93d4b7d269a8735f1b216093e7e9a9fdc4517',
      'condition': 'checkout_android',
  },
}

include_rules = [
  # Everybody can use some things.
  '+include',
  '+unicode',
  '+third_party/fdlibm',
  '+third_party/ittapi/include'
]

# checkdeps.py shouldn't check for includes in these directories:
skip_child_includes = [
  'build',
  'third_party',
]

hooks = [
  {
    # Ensure that the DEPS'd "depot_tools" has its self-update capability
    # disabled.
    'name': 'disable_depot_tools_selfupdate',
    'pattern': '.',
    'action': [
        'python',
        'third_party/depot_tools/update_depot_tools_toggle.py',
        '--disable',
    ],
  },
  {
    # This clobbers when necessary (based on get_landmines.py). It must be the
    # first hook so that other things that get/generate into the output
    # directory will not subsequently be clobbered.
    'name': 'landmines',
    'pattern': '.',
    'action': [
        'python',
        'build/landmines.py',
        '--landmine-scripts',
        'tools/get_landmines.py',
    ],
  },
  # Pull clang-format binaries using checked-in hashes.
  {
    'name': 'clang_format_win',
    'pattern': '.',
    'condition': 'host_os == "win"',
    'action': [ 'download_from_google_storage',
                '--no_resume',
                '--platform=win32',
                '--no_auth',
                '--bucket', 'chromium-clang-format',
                '-s', 'buildtools/win/clang-format.exe.sha1',
    ],
  },
  {
    'name': 'clang_format_mac',
    'pattern': '.',
    'condition': 'host_os == "mac"',
    'action': [ 'download_from_google_storage',
                '--no_resume',
                '--platform=darwin',
                '--no_auth',
                '--bucket', 'chromium-clang-format',
                '-s', 'buildtools/mac/clang-format.sha1',
    ],
  },
  {
    'name': 'clang_format_linux',
    'pattern': '.',
    'condition': 'host_os == "linux"',
    'action': [ 'download_from_google_storage',
                '--no_resume',
                '--platform=linux*',
                '--no_auth',
                '--bucket', 'chromium-clang-format',
                '-s', 'buildtools/linux64/clang-format.sha1',
    ],
  },
  {
    'name': 'gcmole',
    'pattern': '.',
    'condition': 'download_gcmole',
    'action': [ 'download_from_google_storage',
                '--bucket', 'chrome-v8-gcmole',
                '-u', '--no_resume',
                '-s', 'tools/gcmole/gcmole-tools.tar.gz.sha1',
                '--platform=linux*',
    ],
  },
  {
    'name': 'jsfunfuzz',
    'pattern': '.',
    'condition': 'download_jsfunfuzz',
    'action': [ 'download_from_google_storage',
                '--bucket', 'chrome-v8-jsfunfuzz',
                '-u', '--no_resume',
                '-s', 'tools/jsfunfuzz/jsfunfuzz.tar.gz.sha1',
                '--platform=linux*',
    ],
  },
  {
    'name': 'wasm_spec_tests',
    'pattern': '.',
    'action': [ 'download_from_google_storage',
                '--no_resume',
                '--no_auth',
                '-u',
                '--bucket', 'v8-wasm-spec-tests',
                '-s', 'test/wasm-spec-tests/tests.tar.gz.sha1',
    ],
  },
  {
    'name': 'wasm_js',
    'pattern': '.',
    'action': [ 'download_from_google_storage',
                '--no_resume',
                '--no_auth',
                '-u',
                '--bucket', 'v8-wasm-spec-tests',
                '-s', 'test/wasm-js/tests.tar.gz.sha1',
    ],
  },
  {
    'name': 'sysroot_arm',
    'pattern': '.',
    'condition': '(checkout_linux and checkout_arm)',
    'action': ['python', 'build/linux/sysroot_scripts/install-sysroot.py',
               '--arch=arm'],
  },
  {
    'name': 'sysroot_arm64',
    'pattern': '.',
    'condition': '(checkout_linux and checkout_arm64)',
    'action': ['python', 'build/linux/sysroot_scripts/install-sysroot.py',
               '--arch=arm64'],
  },
  {
    'name': 'sysroot_x86',
    'pattern': '.',
    'condition': '(checkout_linux and (checkout_x86 or checkout_x64))',
    'action': ['python', 'build/linux/sysroot_scripts/install-sysroot.py',
               '--arch=x86'],
  },
  {
    'name': 'sysroot_x64',
    'pattern': '.',
    'condition': 'checkout_linux and checkout_x64',
    'action': ['python', 'build/linux/sysroot_scripts/install-sysroot.py',
               '--arch=x64'],
  },
  {
    'name': 'msan_chained_origins',
    'pattern': '.',
    'condition': 'checkout_instrumented_libraries',
    'action': [ 'download_from_google_storage',
                '--no_resume',
                '--no_auth',
                '--bucket', 'chromium-instrumented-libraries',
                '-s', 'third_party/instrumented_libraries/binaries/msan-chained-origins-trusty.tgz.sha1',
              ],
  },
  {
    'name': 'msan_no_origins',
    'pattern': '.',
    'condition': 'checkout_instrumented_libraries',
    'action': [ 'download_from_google_storage',
                '--no_resume',
                '--no_auth',
                '--bucket', 'chromium-instrumented-libraries',
                '-s', 'third_party/instrumented_libraries/binaries/msan-no-origins-trusty.tgz.sha1',
              ],
  },
  {
    # Update the Windows toolchain if necessary.
    'name': 'win_toolchain',
    'pattern': '.',
    'condition': 'checkout_win',
    'action': ['python', 'build/vs_toolchain.py', 'update'],
  },
  {
    # Update the Mac toolchain if necessary.
    'name': 'mac_toolchain',
    'pattern': '.',
    'condition': 'checkout_mac',
    'action': ['python', 'build/mac_toolchain.py'],
  },
  # Pull binutils for linux, enabled debug fission for faster linking /
  # debugging when used with clang on Ubuntu Precise.
  # https://code.google.com/p/chromium/issues/detail?id=352046
  {
    'name': 'binutils',
    'pattern': 'third_party/binutils',
    'condition': 'host_os == "linux"',
    'action': [
        'python',
        'third_party/binutils/download.py',
    ],
  },
  {
    # Note: On Win, this should run after win_toolchain, as it may use it.
    'name': 'clang',
    'pattern': '.',
    # clang not supported on aix
    'condition': 'host_os != "aix"',
    'action': ['python', 'tools/clang/scripts/update.py'],
  },
  {
    'name': 'clang_tidy',
    'pattern': '.',
    'condition': 'checkout_clang_tidy',
    'action': ['python', 'tools/clang/scripts/update.py',
               '--package=clang-tidy'],
  },
  {
    # Update LASTCHANGE.
    'name': 'lastchange',
    'pattern': '.',
    'action': ['python', 'build/util/lastchange.py',
               '-o', 'build/util/LASTCHANGE'],
  },
  {
    'name': 'Download Fuchsia SDK',
    'pattern': '.',
    'condition': 'checkout_fuchsia',
    'action': [
      'python',
      'build/fuchsia/update_sdk.py',
    ],
  },
  {
    'name': 'Download Fuchsia system images',
    'pattern': '.',
    'condition': 'checkout_fuchsia',
    'action': [
      'python',
      'build/fuchsia/update_images.py',
      '--boot-images={checkout_fuchsia_boot_images}',
    ],
  },
  {
    # Mac doesn't use lld so it's not included in the default clang bundle
    # there. However, lld is need in Fuchsia cross builds, so
    # download it there.
    # Should run after the clang hook.
    'name': 'lld/mac',
    'pattern': '.',
    'condition': 'host_os == "mac" and checkout_fuchsia',
    'action': ['python', 'tools/clang/scripts/update.py',
               '--package=lld_mac'],
  },
  {
      # Mac does not have llvm-objdump, download it for cross builds in Fuchsia.
    'name': 'llvm-objdump',
    'pattern': '.',
    'condition': 'host_os == "mac" and checkout_fuchsia',
    'action': ['python', 'tools/clang/scripts/update.py',
               '--package=objdump'],
  },
  # Download and initialize "vpython" VirtualEnv environment packages.
  {
    'name': 'vpython_common',
    'pattern': '.',
    'condition': 'checkout_android',
    'action': [ 'vpython',
                '-vpython-spec', '.vpython',
                '-vpython-tool', 'install',
    ],
  },
  {
    'name': 'check_v8_header_includes',
    'pattern': '.',
    'condition': 'check_v8_header_includes',
    'action': [
      'python',
      'tools/generate-header-include-checks.py',
    ],
  },
]
