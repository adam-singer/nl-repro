# A list of available rules and their signatures can be found here: https://buck2.build/docs/api/rules/

genrule(
    name = "hello_world",
    out = "out.txt",
    cmd = "echo BUILT BY BUCK2> $OUT",
)

genrule(
    name = "node_modules",
    srcs = [
        "package.json",
        "yarn.lock",
    ],
    out = "node_modules",
    cmd = "yarn install && mv node_modules ../out",
    labels = [
        "yarn_install",  # causes this genrule to run locally (needs network access)
    ],
)

genrule(
    name = "tsc_generated",
    srcs = [
        ":node_modules",
        "package.json",
        "tsconfig.json",
    ],
    out = "dist",
    cmd = """\
ls -lh node_modules/ >&2 ; mkdir ${OUT}; echo done > ${OUT}/stamp
""",
    default_outs = ["dist"],
)

