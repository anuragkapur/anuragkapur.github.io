## Jest tests in a babel project - unexpected identifiers
    /Users/anuragkapur/tech-stuff/workspace/zzish/spitafields/src/__tests__/server/utils/utils.test.js:1
    ({"Object.<anonymous>":function(module,exports,require,__dirname,__filename,global,jest){import authToken from "../../../server/utils/authToken";
                                                                                                    ^^^^^^^^^

    SyntaxError: Unexpected identifier

## Resolution
Clean babel build folder before running jest tests