#### META: Title: Ohno Protocol EBNF Specification
#### META: Version: 1.0.0
#### META: Author: Development Team
#### META: PATH: spec/ohno-ebnf.txt

#### SYNOPSIS: Formal EBNF grammar for Ohno Protocol specification
#### SYNOPSIS: Defines complete syntax including file structure, tags
#### SYNOPSIS: Emphasizes mandatory AI-generated SYNOPSIS block
#### SYNOPSIS: Captures three-layer architecture (META, SYNOPSIS, CONTENTS)

#### CONTENTS:

(* Ohno Protocol EBNF v1.0.0 *)

(* Top Level Structure *)
ohnoFile = ohnoOnlyFile | sourceFile;

(* Pure Ohno File Structure *)
ohnoOnlyFile = shebang, newline,
               metaBlock, newline,
               synopsisBlock, newline,
               contentsBlock;

(* Source File Structure *)
sourceFile = [shebang, newline],
            commentBlock?,
            metaBlock, newline,
            synopsisBlock, newline,
            contentsBlock;

(* Three-Layer Architecture *)
metaBlock = metaTag+;              (* Layer 1: Human Metadata *)
synopsisBlock = synopsisTag+;      (* Layer 2: AI Analysis *)
contentsBlock = section*;          (* Layer 3: Human Content *)

(* Header Components *)
metaTag = tagLevel4, "META:", whitespace, key, ":", whitespace, value, newline;
synopsisTag = tagLevel4, "SYNOPSIS:", whitespace, aiGeneratedText, newline;
contentsTag = tagLevel4, "CONTENTS:", newline;

(* Section Structure *)
section = sectionStart, content, sectionEnd;
sectionStart = tagLevel3, "SECTION:", whitespace, identifier, newline;
sectionEnd = tagLevel3, "END:", whitespace, "SECTION:", whitespace, identifier, newline;

(* Comment Syntax *)
commentBlock = blockStart, newline,
               (ohnoLine | otherLine)*,
               blockEnd, newline;

blockStart = "/*" | "<!--" | "{-";
blockEnd = "*/" | "-->" | "-}";

(* Task Tags *)
todoTag = tagLevel3, "TODO:", whitespace, text, newline;
doneTag = tagLevel3, "DONE:", whitespace, timestamp, newline;
fixmeTag = tagLevel3, "FIXME:", whitespace, text, newline;
ideaTag = tagLevel3, "IDEA:", whitespace, text, newline;
reviewTag = tagLevel3, "REVIEW:", whitespace, text, newline;
noteTag = tagLevel3, "NOTE:", whitespace, text, newline;
triageTag = tagLevel3, "TRIAGE:", whitespace, text, newline;

(* Analysis Tags *)
metricsTag = tagLevel3, "METRICS:", (whitespace, metricValue)+, newline;
tagsTag = tagLevel3, "TAGS:", (whitespace, identifier)+, newline;
functionTag = tagLevel3, "FUNCTION:", whitespace, functionDef, newline;
linkTag = tagLevel3, "LINK:", whitespace, reference, newline;

(* Extension Tags *)
extensionTag = tagLevel3, "@", namespace, "::", tag, ":", whitespace, text, newline;

(* Data Formats *)
metricValue = number, [unit];
number = [currencySymbol], digits, [".", digits];
timestamp = digits, "/", digits, "/", digits,
           [whitespace,
           digits, ":", digits];

(* Reference Format *)
reference = [pathPrefix], path, [":", lineNum], ["#", identifier];
pathPrefix = "./" | "../" | "/";
path = (identifier, "/")*, identifier;
lineNum = digits;

(* Basic Elements *)
shebang = "#!", nonNewlineChars;
identifier = letter, (letter | digit | "-" | "_")*;
key = uppercase+;
value = nonNewlineChars;
text = nonNewlineChars;
aiGeneratedText = nonNewlineChars;  (* Must be AI-generated *)
whitespace = " "+;
newline = "\n";
letter = "A" | ... | "Z" | "a" | ... | "z";
digit = "0" | ... | "9";
uppercase = "A" | ... | "Z";
currencySymbol = "$" | "£" | "€" | "USD" | "GBP" | "EUR";
unit = "%" | "mins" | "hrs" | "days" | identifier;
namespace = uppercase+;

(* Utility *)
nonNewlineChars = {anyCharExceptNewline}+;
anyCharExceptNewline = ? any character except newline ?;

(* Comments *)
ohnoLine = ? line containing Ohno tag ?;
otherLine = ? line without Ohno tag ?;

(* Tag Levels *)
tagLevel4 = "####", whitespace;
tagLevel3 = "###", whitespace;